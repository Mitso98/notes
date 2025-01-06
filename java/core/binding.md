# Binding in Java

## Static Binding (Early Binding)
- **Description**: Static binding occurs at compile time. It is associated with method overloading and private, static, and final methods, as these methods cannot be overridden.
- **Example**:
```java
class StaticBindingExample {
    private void display() {
        System.out.println("Private method in StaticBindingExample");
    }

    public static void main(String[] args) {
        StaticBindingExample obj = new StaticBindingExample();
        obj.display();
    }
}
```

## Dynamic Binding (Late Binding)
- **Description**: Dynamic binding occurs at runtime. It is associated with method overriding, where the method to be called is determined at runtime based on the object's actual type.
- **Example**:
```java
class Parent {
    void display() {
        System.out.println("Method in Parent class");
    }
}

class Child extends Parent {
    @Override
    void display() {
        System.out.println("Method in Child class");
    }

    public static void main(String[] args) {
        Parent obj = new Child();
        obj.display(); // Output: Method in Child class
    }
}
```

## Method Overloading
- **Description**: Method overloading occurs when multiple methods in the same class have the same name but different parameters (different type, number, or both). It is an example of static binding.
- **Example**:
```java
class OverloadingExample {
    void display(int a) {
        System.out.println("Method with integer argument: " + a);
    }

    void display(String a) {
        System.out.println("Method with string argument: " + a);
    }

    public static void main(String[] args) {
        OverloadingExample obj = new OverloadingExample();
        obj.display(10);
        obj.display("Hello");
    }
}
```

## Method Overriding
- **Description**: Method overriding occurs when a subclass provides a specific implementation of a method that is already defined in its superclass. It is an example of dynamic binding.
- **Example**:
```java
class SuperClass {
    void display() {
        System.out.println("Method in SuperClass");
    }
}

class SubClass extends SuperClass {
    @Override
    void display() {
        System.out.println("Method in SubClass");
    }

    public static void main(String[] args) {
        SuperClass obj = new SubClass();
        obj.display(); // Output: Method in SubClass
    }
}
```

## Relations between Static Binding, Dynamic Binding, Method Overloading, and Method Overriding
- **Static Binding**:
  - Occurs at compile time.
  - Associated with method overloading.
  - Used for private, static, and final methods.
- **Dynamic Binding**:
  - Occurs at runtime.
  - Associated with method overriding.
  - Used for instance methods that can be overridden in subclasses.
- **Method Overloading**:
  - Allows multiple methods with the same name but different parameters in the same class.
  - Example of static binding.
- **Method Overriding**:
  - Allows a subclass to provide a specific implementation of a method already defined in its superclass.
  - Example of dynamic binding.
