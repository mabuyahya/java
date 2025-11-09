### java VS c++
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