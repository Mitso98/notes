# Java Notes

## Method Overriding

**Purpose:**
Allows subclass to provide specific implementation to a method that exists in super class while retaining the same method signature.

**Key points:**
- **Same Method Signature:** The method in the subclass must have the same name, return type (or subtype), and parameters as the method in the superclass, otherwise you will be doing method overloading in different classes which will cause issues.
- **@Override Annotation:** Though optional, it’s a good practice to use the @Override annotation, which ensures that the method is indeed overriding the parent method.
- **Access Modifiers:** The overridden method cannot have a more restrictive access modifier than the method in the superclass. For example, if the superclass method is public, the subclass method must also be public (or protected, but not private).
- **Non-final Methods:** Only methods that are not marked final can be overridden. If a method is final, it cannot be overridden in any subclass.
- **Instance Methods:** Only instance (non-static) methods can be overridden. Static methods belong to the class and not to instances, so they cannot be overridden (though they can be hidden with method hiding).
- **Constructor:** Constructors cannot be overridden because they are not inherited by subclasses.
- **Super Keyword:** Use `super.methodName()` to call the superclass version of the overridden method if you want to reuse some behavior.
- **Overriding with Covariant Return Types:** You can override a method and change its return type to a subclass of the original return type. For instance, a method returning Animal can be overridden to return Dog.
- **Leverage Polymorphism:** Overriding is a key concept in polymorphism. If you use a parent class reference pointing to a child object, the child’s overridden method will be executed.
- **Check Final and Private Methods:** Make sure the method is not final or private, as these cannot be overridden.
- **Exception Handling:** When overriding, the new method cannot throw broader checked exceptions than the method in the superclass. For example, if the superclass method throws an IOException, the subclass can throw IOException or any of its subclasses but not Exception (which is broader).

The restriction exists to maintain:
- **Code safety:** Prevents introducing new, unrelated exceptions that client code is not prepared for.
- **Predictability:** Ensures that overridden methods behave as expected with respect to exceptions.
- **Substitutability:** Ensures that a subclass can replace a superclass without changing how the method is called or handled (Liskov substitute).
- **Cleaner, more maintainable code:** By limiting broader exceptions, the program remains more focused and easier to understand.

## Method Overloading

**Purpose:**
Occurs when multiple methods in the same class share the same name but differ in the number or types of parameters. It allows methods to perform similar tasks but with different inputs.

**Key Points of Method Overloading:**
- **Different Parameters:** Methods must have different parameter lists (either in number, type, or both) to be overloaded.
- **Return Type:** The return type can be different, but overloading is not determined by the return type alone. The parameter list is what distinguishes overloaded methods.
- **Same Class:** Overloading occurs within the same class. However, methods from a superclass can also be overloaded in a subclass.
- **Compile-Time Polymorphism:** Overloading is a form of compile-time (or static) polymorphism because the method to be invoked is determined at compile time based on the method signature.
- **Varargs:** You can use varargs (...) to overload a method that accepts a varying number of arguments. For example, `public void method(String... args)` will accept any number of String arguments.
- **Avoid Ambiguity:** Be careful of ambiguous calls, especially when overloading with similar parameter types (e.g., int and long). The compiler may not know which version to invoke, especially when literals are involved.
- **Leverage Autoboxing:** Overloaded methods can leverage autoboxing and unboxing to convert between primitive types and their wrapper classes (int to Integer, double to Double, etc.). Keep in mind, this can sometimes cause ambiguity if not handled carefully.
- **Method Chaining:** Overloading can be used to support method chaining with different types of arguments, making your code flexible and reusable.
- **Keep Overloading Simple:** Avoid overloading too many similar methods, as it can reduce code clarity and make debugging more difficult.

## Polymorphism

- **Compile-time polymorphism (static/early binding):** Achieved by overloading.
- **Run-time Polymorphism (Dynamic/late Binding):** Achieved through method overriding.

**Dynamic method dispatch:** It happens when a superclass reference variable holds an object of a subclass, and the method that gets executed is determined based on the actual object type at runtime.

```java
A obj = new A();  // in show A
obj = new B();    // in show B
obj = new C();    // in show C
```

## Final

- **final variable:** Its value cannot be changed once assigned it can be declared without assignment when it is assigned to the constructor.
- **final method:** Cannot be overridden by subclasses.
- **final class:** Cannot be subclassed.

## Abstract class

An abstract class in Java is a class that cannot be instantiated and is meant to be extended by other classes. It can contain both abstract methods (without a body) and concrete methods (with an implementation). Abstract methods must be implemented by any non-abstract subclass.

Although an abstract class cannot be instantiated, it has a constructor, because it is called once it is inherited.

**Key points:**
- Defined using the `abstract` keyword.
- Can have constructors, fields, and methods (both abstract and concrete).
- Used when you want to provide a common base and some implementation while forcing subclasses to complete the rest.

## Interface

In Java, an interface is a reference type used to define a contract that classes must follow. It can contain method declarations (abstract methods), default methods (with a body), static methods, and constants (public, static, final fields). A class that implements an interface must provide implementations for all its abstract methods.

**Key points:**
- Defined using the `interface` keyword.
- All methods in an interface are public and abstract by default (except default and static methods).
- A class can implement multiple interfaces, allowing Java to support multiple inheritance of behavior.
- Interfaces provide a way to achieve loose coupling by specifying behavior without enforcing a specific implementation.
- Properties of interface are static because we cannot instantiate an interface.
- Properties are final because the interface does not have any memory in the heap so how can you have a non-final variable if it does not have a memory?
- We use `extends` keyword if an interface needs to inherit another interface.
  - Interface extends interface.
  - Class implements interface.
  - Class extends class.

**Types:**
- Normal
- Functional (SAM): It makes great synergy with anonymous class & lambda expression.
- Marker: Helps serialize & deserialize data.

## Class loader

- Part of the Java Runtime Environment (JRE).
- Dynamically loads Java classes into the Java Virtual Machine (JVM) during runtime.
- It is responsible for finding and loading class files when they are referenced in the code.

## New Keyword

- Used to create new objects or instances of classes.
- When you use `new`, it allocates memory for a new object during runtime on the heap and returns a reference to that memory.
- This reference is typically assigned to a variable of the class type.
- Invokes the constructor of the class to initialize the new object.

## Anonymous object

- When you create an object using the `new` keyword without a name it’s called an anonymous object:
  ```java
  new Object();
  new Object().method();  // valid syntax
  ```
- The problem is that you can’t reuse anonymous objects. 👎
- It’s useful for one-time use objects, and they are typically garbage collected as soon as they go out of scope, so it’s useful for reducing memory consumption. 👍

## Enums

They are a special type of class, they implicitly extend Object. They can have properties, methods, and constructors. Notice enum constructor is private because we use it only inside the class. There is no default constructor for enum.























