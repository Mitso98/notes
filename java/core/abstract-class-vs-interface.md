## Abstract Class vs Interface in Java

### Abstract Class
An abstract class is a class that cannot be instantiated on its own and must be subclassed. It can have both abstract methods (without implementation) and concrete methods (with implementation).

#### Key Points:
- Can have both abstract and concrete methods.
- Can have member variables.
- Can have constructors.
- Supports inheritance (a class can extend only one abstract class).
- Can provide a common base class for related classes.

#### Example:
```java
abstract class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    abstract void makeSound();

    void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + " says: Woof Woof");
    }
}
```

### Interface
An interface is a reference type in Java, similar to a class, that can contain only constants, method signatures, default methods, static methods, and nested types. Interfaces cannot have instance fields or constructors.

#### Key Points:
- Can only have abstract methods (until Java 8, which introduced default and static methods).
- Cannot have member variables (only constants).
- Cannot have constructors.
- Supports multiple inheritance (a class can implement multiple interfaces).
- Used to define a contract that implementing classes must follow.

#### Example:
```java
interface Animal {
    void makeSound();
    void sleep();
}

class Dog implements Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof Woof");
    }

    @Override
    public void sleep() {
        System.out.println("Dog is sleeping.");
    }
}
```

### Performance and Memory Considerations
- **Abstract Class**: Since abstract classes can have concrete methods and member variables, they may consume more memory compared to interfaces. The performance impact is generally minimal, but the memory footprint can be higher due to the storage of state (member variables).
- **Interface**: Interfaces are typically lighter in terms of memory usage because they do not hold state. However, the use of multiple interfaces can lead to a slight increase in the complexity of the method dispatch mechanism, which might have a negligible impact on performance.

In summary, the choice between abstract classes and interfaces should be guided by the design requirements of your application. Use abstract classes when you need to share code among closely related classes, and use interfaces to define a contract that can be implemented by any class, regardless of its position in the class hierarchy.
