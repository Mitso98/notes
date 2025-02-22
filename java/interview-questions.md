# What is Java?

Java is a high-level, class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible. It is a general-purpose programming language intended to let application developers write once, run anywhere (WORA).

# What are the main features of Java?

- Simple
- Object-Oriented
- Portable
- Platform independent
- Secured
- Robust
- Multithreaded
- Architecture neutral
- Interpreted
- High Performance
- Distributed
- Dynamic

# What is the difference between JDK, JRE, and JVM?

**JDK (Java Development Kit):** It is a software development kit used to develop Java applications. It includes JRE, an interpreter/loader (Java), a compiler (javac), an archiver (jar), a documentation generator (Javadoc), and other tools needed for Java development.

**JRE (Java Runtime Environment):** It provides libraries, Java Virtual Machine (JVM), and other components to run applications written in Java. JRE is the implementation of JVM.

**JVM (Java Virtual Machine):** It is an abstract machine that provides a runtime environment in which Java bytecode can be executed. JVMs are available for many hardware and software platforms.

# What is a Class in Java?

A class is a blueprint from which individual objects are created. A class can contain fields and methods to describe the behavior of an object.

# What is an Object in Java?

An object is an instance of a class. It has a state and behavior. The state is represented by attributes (fields) and the behavior is represented by methods.

# What is Inheritance in Java?

Inheritance is a mechanism wherein a new class is derived from an existing class. The new class inherits the fields and methods of the existing class. It promotes code reusability.

# What is Polymorphism in Java?

Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance. There are two types of polymorphism in Java: compile-time polymorphism (method overloading) and runtime polymorphism (method overriding).

# What is Encapsulation in Java?

Encapsulation is the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates, and keeps both safe from outside interference and misuse.

# What is Abstraction in Java?

Abstraction is the process of hiding the implementation details and showing only the functionality to the user. It helps in reducing programming complexity and effort.

# What is the difference between an Interface and an Abstract class in Java?

**Abstract Class:** Can have abstract and non-abstract methods, can have instance variables, can provide the implementation of an interface, and can have constructors.

**Interface:** Can have only abstract methods (until Java 8, after which default and static methods are allowed), cannot have instance variables, cannot provide the implementation of an abstract class, and cannot have constructors.

# What is the difference between method overloading and method overriding in Java?

**Method Overloading:** It occurs when two or more methods in the same class have the same name but different parameters. It is a compile-time polymorphism.

**Method Overriding:** It occurs when a subclass has a method with the same name and parameters as a method in its superclass. It is a runtime polymorphism.

# What is the use of the 'super' keyword in Java?

The 'super' keyword in Java is used to refer to the immediate parent class object. It can be used to call parent class methods, access parent class fields, and call the parent class constructor.

# What is a Constructor in Java?

A constructor in Java is a block of code that initializes a newly created object. It has the same name as the class and does not have a return type. Constructors can be overloaded.

# What is the difference between '== operator' and 'equals() method' in Java?

**'== operator':** It is used to compare the references of two objects, i.e., whether they point to the same memory location.

**'equals() method':** It is used to compare the contents of two objects, i.e., whether they are logically equal.

# What is the purpose of garbage collection in Java?

Garbage collection in Java is the process of automatically freeing memory by destroying objects that are no longer reachable in the program. It helps in preventing memory leaks and optimizing memory usage.

# What is the 'final' keyword in Java?

The 'final' keyword in Java is used to restrict the user. It can be used in three contexts:
- **Final variable:** Its value cannot be changed once assigned.
- **Final method:** It cannot be overridden by subclasses.
- **Final class:** It cannot be subclassed.

# What is Exception Handling in Java?

Exception handling in Java is a mechanism to handle runtime errors, allowing the normal flow of the program to be maintained. It is done using five keywords: try, catch, finally, throw, and throws.

# What is a Thread in Java?

A thread in Java is a lightweight process that allows concurrent execution of two or more parts of a program. Threads can be created by implementing the Runnable interface or extending the Thread class.

# What is the difference between 'ArrayList' and 'LinkedList' in Java?

**ArrayList:** It is a resizable array implementation of the List interface. It provides fast random access but slow insertion and deletion operations.

**LinkedList:** It is a doubly-linked list implementation of the List interface. It provides fast insertion and deletion operations but slow random access.

# What is the Java Collections Framework?

The Java Collections Framework is a set of classes and interfaces that implement commonly reusable collection data structures such as lists, sets, and maps. It provides algorithms to manipulate the collections and allows interoperability among different collection types.

# What is a Lambda Expression in Java?

A lambda expression is a feature introduced in Java 8 that allows you to write anonymous methods. It provides a clear and concise way to represent one method interface using an expression. Lambda expressions are used primarily to define the inline implementation of a functional interface.

# What is a Stream in Java?

A stream is a sequence of elements supporting sequential and parallel aggregate operations. Streams are introduced in Java 8 and are used to process collections of objects. A stream is not a data structure but a view of the data.

# What is the difference between 'synchronized' and 'volatile' keywords in Java?

**synchronized:** It is used to control the access of multiple threads to a shared resource. It can be applied to methods or blocks of code to ensure that only one thread can execute the synchronized code at a time.

**volatile:** It is used to indicate that a variable's value will be modified by different threads. It ensures that the value of the volatile variable is always read from the main memory and not from the thread's local cache.

# What is the difference between 'wait()' and 'sleep()' methods in Java?

**wait():** It is used to pause the execution of the current thread until another thread notifies it to wake up. It is called on an object and must be used within a synchronized block or method.

**sleep():** It is used to pause the execution of the current thread for a specified period. It is called on a thread and does not require synchronization.

# What is the 'transient' keyword in Java?

The 'transient' keyword in Java is used to indicate that a field should not be serialized. When an object is serialized, the transient fields are not included in the serialized representation.

# What is the 'default' keyword in Java?

The 'default' keyword in Java is used to define default methods in interfaces. Default methods are methods with a body that can be added to interfaces without breaking the implementing classes.

# What is the 'Optional' class in Java?

The 'Optional' class is a container object introduced in Java 8 that may or may not contain a non-null value. It is used to represent optional values and helps in avoiding null pointer exceptions.

# What is the 'Functional Interface' in Java?

A functional interface is an interface that contains exactly one abstract method. It can have any number of default or static methods. Functional interfaces are used primarily for lambda expressions and method references.

# What is the 'Stream API' in Java?

The Stream API is a feature introduced in Java 8 that provides a functional approach to processing collections of objects. It allows you to perform operations such as filtering, mapping, and reducing on collections in a declarative manner.

# What is the 'CompletableFuture' class in Java?

The 'CompletableFuture' class is a feature introduced in Java 8 that represents a future result of an asynchronous computation. It provides methods to handle the result of the computation and allows you to chain multiple asynchronous operations.

# What is the 'Nashorn' JavaScript Engine in Java?

The 'Nashorn' JavaScript engine is a feature introduced in Java 8 that allows you to execute JavaScript code from within Java applications. It provides better performance and compliance with the ECMAScript specification compared to the previous JavaScript engine.

# What is the 'Jigsaw' Project in Java?

The 'Jigsaw' project is a feature introduced in Java 9 that aims to modularize the Java platform. It introduces the Java Platform Module System (JPMS) that allows you to create and use modules, improving the maintainability and scalability of Java applications.

# What is the 'Var' keyword in Java?

The 'var' keyword is a feature introduced in Java 10 that allows you to declare local variables with inferred types. It provides a more concise way to declare variables without explicitly specifying their types.

# What is the 'Text Blocks' feature in Java?

The 'Text Blocks' feature is a feature introduced in Java 13 that allows you to create multi-line string literals in a more readable and maintainable way. It uses triple quotes to define the text block and preserves the formatting of the text.

# What is the 'Records' feature in Java?

The 'Records' feature is a feature introduced in Java 14 that provides a concise way to define immutable data classes. Records automatically generate boilerplate code such as constructors, getters, equals(), hashCode(), and toString() methods.

# What is the 'Pattern Matching' feature in Java?

The 'Pattern Matching' feature is a feature introduced in Java 16 that allows you to use pattern matching in instanceof expressions. It simplifies the code by eliminating the need for explicit type casting.

# What is the 'Sealed Classes' feature in Java?

The 'Sealed Classes' feature is a feature introduced in Java 17 that allows you to restrict which classes can extend or implement a class or interface. It provides more control over the inheritance hierarchy and improves the maintainability of the code.

# What is the 'Z Garbage Collector' (ZGC) in Java?

The 'Z Garbage Collector' (ZGC) is a scalable low-latency garbage collector introduced in Java 11. It is designed to handle large heaps with minimal pause times, making it suitable for applications requiring high throughput and low latency.

# What is the 'Foreign Function & Memory API' in Java?

The 'Foreign Function & Memory API' is a feature introduced in Java 16 that allows Java programs to interoperate with code and data outside of the Java runtime. It provides a way to call native libraries and access native memory in a safe and efficient manner.

# What is the 'Vector API' in Java?

The 'Vector API' is a feature introduced in Java 16 that provides a way to express vector computations that can be reliably compiled at runtime to optimal vector hardware instructions on supported CPU architectures. It aims to improve the performance of data-parallel operations.

# What is the 'Project Loom' in Java?

'Project Loom' is an ongoing project aimed at introducing lightweight, user-mode threads (fibers) to the Java platform. It aims to simplify concurrent programming by providing a more efficient and scalable way to handle many threads.

# What is the 'Project Panama' in Java?

'Project Panama' is an ongoing project aimed at improving the connection between Java and native code. It focuses on providing a more efficient and user-friendly way to access native libraries and data structures from Java.

# What is the 'Project Valhalla' in Java?

'Project Valhalla' is an ongoing project aimed at introducing value types to the Java platform. Value types are immutable data types that do not have identity, allowing for more efficient memory layout and performance improvements.

# What is the 'Project Amber' in Java?

'Project Amber' is an ongoing project aimed at improving developer productivity by introducing smaller, productivity-oriented language features to Java. Examples include pattern matching, records, and local variable type inference.

# What is the 'GraalVM' in Java?

'GraalVM' is a high-performance runtime that provides support for multiple programming languages and execution modes. It includes a just-in-time (JIT) compiler and an ahead-of-time (AOT) compiler, enabling improved performance and interoperability between languages.

# What is the 'JEP' process in Java?

The 'JEP' (JDK Enhancement Proposal) process is a way to propose, review, and track significant changes to the Java platform. Each JEP describes a new feature or enhancement, providing details on its motivation, design, and implementation.

# What is the 'JMH' (Java Microbenchmark Harness) in Java?

The 'JMH' (Java Microbenchmark Harness) is a framework for writing, running, and analyzing microbenchmarks in Java. It is designed to measure the performance of small code snippets with high precision and accuracy.

# What is the 'JFR' (Java Flight Recorder) in Java?

The 'JFR' (Java Flight Recorder) is a profiling and event collection framework built into the Java Virtual Machine (JVM). It allows developers to collect detailed information about the runtime behavior of Java applications with minimal overhead.

# What is the 'JLink' tool in Java?

The 'JLink' tool is a feature introduced in Java 9 that allows developers to create custom runtime images containing only the modules and dependencies required by their applications. It helps in reducing the size of the runtime and improving startup time.

# What is the 'JPackage' tool in Java?

The 'JPackage' tool is a feature introduced in Java 14 that allows developers to create native installers and packages for their Java applications. It supports various packaging formats, including MSI, EXE, DMG, and RPM, making it easier to distribute and install Java applications.

# What is the 'JEP 330' (Launch Single-File Source-Code Programs) in Java?

'JEP 330' is a feature introduced in Java 11 that allows developers to run single-file source-code programs without the need for compilation. It simplifies the development and testing of small programs and scripts by allowing them to be executed directly from the source file.

# What is the 'JEP 355' (Text Blocks) in Java?

'JEP 355' is a feature introduced in Java 13 that provides a new syntax for defining multi-line string literals, known as text blocks. Text blocks make it easier to write and maintain multi-line strings by preserving their formatting and reducing the need for escape sequences.
