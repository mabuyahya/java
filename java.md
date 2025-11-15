
### java VS c++
the main differences that the java uses a virtual machine (JVM) to run the code which makes big difference also java is a fully object-oriented language.
- Java is a high-level, object-oriented programming language developed by Sun Microsystems (now owned by Oracle) in 1995.
- C++ is a general-purpose programming language that was developed by Bjarne Stroustrup at Bell Labs in 1979.
- Java is platform-independent at the source and binary levels, while C++ is platform-dependent.
- Java has automatic garbage collection, while C++ requires manual memory management.
- Java is generally considered easier to learn and use, while C++ offers more control over system resources and memory.

### java compilation according to c++
- Java code is compiled into bytecode (not machine code) using the Java compiler (javac), which is executed by the Java Virtual Machine (JVM). This allows Java to be platform-independent, as the same bytecode can run on any system with a compatible JVM.
- C++ code is compiled directly into machine code specific to the target platform. This means that C++ programs need to be recompiled for each different platform they are intended to run on.

### basic structure of java program
- in java every code is written inside a class
- the main method is the entry point of any java program
- the class name should match the file name

### java data types
- Primitive Data Types: byte(8), short(16), int(32), long(64), float(32), double(64), char(16), boolean(1)
- String: In Java, all string literals are objects of the String class("hello world".length()). not like c++ where string is an array of characters.
- in java using an uninitialized variable will give a compilation error.
- in java for every primitive data type there is a corresponding wrapper class (byte -> Byte, short -> Short, int -> Integer, long -> Long, float -> Float, double -> Double, char -> Character, boolean -> Boolean), these classes provide useful methods for converting between types and manipulating values.

### java things
- in java there are no pointers only references.
- in java there are no pointers thats pointer to the heap, but in java every object is stored in the heap
- in java every object variable is a reference to the object in the heap
- the object name itself is a reference to the object in the heap without the need of using '&' or * operator
- all the objects in java are created using the 'new' keyword, unlike primitive data types which can be created without using 'new' 
- in java there is no need to manually free the memory allocated to objects, java has an automatic garbage collector that takes care of freeing memory that is no longer needed
- all classes derive from the Object class by default.
in java:
No header files → no need for separate declaration/definition
Everything is in .java file — both interface and implementation
Compilation model is different: JVM uses bytecode, not direct linking

``` java
Person p = new Person("Alice");
```
even though p looks like a regular variable, it’s really just holding a reference (a managed pointer), and the object is always on the heap.
and when passing p as an argument  a copy of the pointer (address) is passed — not a copy of the object.

### java functions
- in java functions are called methods and they are always defined inside a class
- in java no need to forward declare methods before using them
- all primitive data types are passed by value, while objects are passed by reference
- method overloading is supported in java, allowing multiple methods with the same name but different parameter, but no operator overloading

### java packages
- packages are used to group related classes and interfaces together, providing a namespace management mechanism
- the java standard library is organized into packages, such as java.lang, java.util, and java.io, each containing related classes and interfaces
- to use a class from a package, you need to import it using the 'import' statement
- you can create your own packages by using the 'package' keyword at the beginning of your source file.

### Strings
in c++ when we create a string using double quotes, it creates a string literal which is stored in a read-only section of memory. Modifying a string literal results in undefined behavior.
``` c++
char* str = "Hello"; // string literal
``` 
also in c++ there are a srting class in the standard library that can be used to create strings.
``` c++
#include <string>
std::string str = "Hello"; // string object
```
here the c++ compiler buted "hello" in a read-only section of memory then called the string constructor (this constructor allocates memory on the heap and copies the contents of the string literal into that memory)
in java everything is different, in java when we create a string using double quotes, it creates a String object and stores it in the heap memory in a special area called the string pool. when using a string literal in c++ the compiler creates a array of characters in a read-only section of memory, but in java the compiler creates a String object in the heap memory. and return a reference to that object.
``` java
String str = "Hello"; // String object
```
first the java compiler checks the string pool to see if a string with the same value already exists. If it does, it simply returns a reference to that existing string. If not, it creates a new String object in the heap memory and adds it to the string pool.
no constructor is called here because the java compiler automatically creates the String object for us when we use double quotes.
what if a want to create a string and don't want to use the string pool?
``` java
String str = new String("Hello"); // String object not in string pool
```
here the java compiler creates a new String object in the heap memory regardless of whether a string with the same value already exists in the string pool or not. what is really happening here is that the java compiler first creates a string literal "Hello" in the string pool (if it doesn't already exist), then it calls the String constructor to create a new String object in the heap memory and copies the contents of the string literal into that object.

### arrays in java
in c++ arrays can be created in the stack or in the heap.(in the end array variable are just pointers to a block of memory)
in java the array variable is a reference to an array object in the heap memory(an object is created in the heap because this is how java creates object).
this object contains the array elements and some metadata about the array (such as its length).
``` java
int[] arr = new int[5]; // array object in heap
```
here the java compiler creates an array object in the heap memory that can hold 5 integers and returns a reference to that object.

### Packages in java
packages in java are similar to namespaces in c++. but with enforces sturcture on the file system.
in c++ namespaces are used to group related classes, functions, and variables together to avoid naming conflicts.
in java packages are used to group related classes and interfaces together, providing a namespace management mechanism.
packages in java also enforce a directory structure on the file system. for example if we have a package named com.example.myapp, the corresponding directory structure would be com/example/myapp.
``` java
package com.example.myapp;
```

### access specifiers in java
- public: The member is accessible from any other class.
- protected: The member is accessible within its own package and by subclasses.
- default (no modifier): The member is accessible only within its own package.
- private: The member is accessible only within its own class.
- static: The member belongs to the class rather than to any specific instance of the class.(getting created once and shared among all instances of the class)
- static methods can be called without creating an instance of the class. (static methods cannot access instance variables or methods directly; they can only access static variables and methods)

### inheritance in java
Inheritance allows one class (subclass / derived class) to reuse fields and methods from another class (superclass / base class)
in java, only single inheritance is allowed for classes, not like c++ where multiple inheritance is allowed(and the diamond problem may occur).
use extends keyword to inherit from a class.
all methods are virtual by default in java, so no need to use virtual keyword.(which makes polymorphism easier to implement).
the base class constructor must be called explicitly using super() in the derived class constructor.
``` java
class Animal {
    int age;
    void printAge() {
        System.out.println("Animal age: " + age);
    }
}

class Dog extends Animal {
    int breed;
    void printBreed() {
        System.out.println("Dog breed: " + breed);
    }
}

class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.printAge();
        myDog.printBreed();
    }
}
```
first we have a base class Animal which has the age field and the printAge(Animal *age) method.
second we have a derived class Dog which inherits from Animal using the extends keyword. Dog has its own field breed and method printBreed().
when a class inherits from another class, what is really happening that when creating an object of the derived class also the base class filds get created as well and comes first before the derived class fields in the memory layout of the object.
so when we create an object of Dog, it contains both the age field from Animal and the breed field from Dog.
and the drived class can access the base class methods directly.(because the amimal part of the object is there in the dog object and comes first so the this method printAge(Animal *age) works when the dog object calls it because the dog object contains the animal part).

### polymorphism in java
polymorphism allows methods to do different things based on the object not in the variable that the object is stored in.
in java all methods are virtual by default, so no need to use the virtual keyword like in c++.
to override a method in the derived class, simply define a method with the same name and signature in the derived class.
``` java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

class Main {
    public static void main(String[] args) {
        Animal myAnimal;
        myAnimal = new Dog();
        myAnimal.sound();
        myAnimal = new Cat();
        myAnimal.sound();
    }
}
```
here we have a base class Animal with a method sound().
we have two derived classes Dog and Cat that override the sound() method to provide their own implementations.
in the main method, we create a reference variable of type Animal and assign it to different derived class objects (Dog and Cat).
when we call the sound() method on the myAnimal reference, the appropriate overridden method is invoked based on the actual object type (Dog or Cat) at runtime, demonstrating polymorphism.