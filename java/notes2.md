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

## DI injection methods in spring boot

### Constructor Injection

**Description:** Dependencies are provided through the class constructor. Spring injects the dependencies when it instantiates the bean.

**Pros:**
- Ensures immutability since dependencies are provided at object creation and cannot be changed afterward.
- Makes the dependencies explicit and easy to understand.
- Dependencies are required to instantiate the object, reducing the chances of null values.
- Ideal for mandatory dependencies.
- Detects circular dependencies early.

**Cons:**
- Can become cumbersome with too many dependencies, leading to long constructors.

### Setter Injection

**Description:** Dependencies are injected via public setter methods after the object is created.

**Pros:**
- Useful for optional dependencies, since you can choose whether or not to set the dependency.
- More flexible, allowing you to change the dependencies later.
- Avoids cluttered constructors in case of too many dependencies.

**Cons:**
- Does not guarantee immutability, as the dependencies can be changed after object creation.
- The object can be in an incomplete state if the setter is not called, leading to potential NullPointerExceptions.
- Less suitable for required dependencies.

### Field Injection

**Description:** Dependencies are injected directly into the class fields, usually by annotating the fields with `@Autowired`.

**Pros:**
- Very simple to use and less boilerplate code (no need for setters or constructors).

**Cons:**
- Violates encapsulation since the dependencies are not set through constructors or setters, but directly injected into the fields.
- Harder to test: Mocking and injecting dependencies in unit tests is more difficult.
- Dependencies are less visible, making it harder to understand what the class depends on.
- Immutability is not ensured since fields can be modified post-construction.
- Not ideal for required dependencies, as it can lead to uninitialized or null values.
- Spring discourages field injection due to its downsides, like violating best practices in object-oriented design.

## Bean Scope

- **Singleton:** Only one object gets created when you use `getBean`.
- **Prototype:** Different object is created every time you use `getBean`.
- **Request**
- **Session**

## JSP

Spring Boot does not support JSP by default, we have to install Tomcat Jasper same version of Tomcat Jasper as Tomcat server that we will use to convert JSP to servlet.

**Spring Boot does not support JSP by default:**
Spring Boot prefers using Thymeleaf or Freemarker for rendering views because JSP has several limitations when working with embedded servlet containers (like the embedded Tomcat Spring Boot uses by default). JSP requires specific servlet handling and configurations which don't work well with Spring Boot's default setup.

**Tomcat Jasper for JSP compilation:**
To use JSP with Spring Boot, you do need Jasper, the JSP engine for Apache Tomcat. Spring Boot does not include the Jasper dependency by default, so you'll need to add it manually. You need to include the `tomcat-jasper` dependency in your `pom.xml` (for Maven) or `build.gradle` (for Gradle). The version of `tomcat-jasper` should match the version of the embedded Tomcat that Spring Boot uses. If you are using an external Tomcat server (not the embedded one), the version should align with that.

**Limitations of JSP with Spring Boot:**
- JSP files need to be placed in `src/main/webapp/WEB-INF/jsp/`, and you might need to customize your ViewResolver bean.
- Some features like hot reloading may not work as smoothly with JSP, especially when using embedded containers.

In summary: yes, you need Tomcat Jasper for JSP compilation, but keep in mind that using JSP with Spring Boot is not recommended, and it might require additional setup and careful handling.

## Aspect-Oriented Programming (AOP)

Aspect-Oriented Programming (AOP) is a programming paradigm that helps in separating cross-cutting concerns from the main business logic. Here's a breakdown of the core AOP concepts:

1. **Aspect:** An aspect encapsulates a concern that cuts across multiple classes or modules. For example, logging, security, or transaction management. It contains the logic that is applied to multiple points in an application.
2. **Join Point:** A specific point in the execution of the program where an aspect can be applied. Examples include method calls, object instantiations, or field access.
3. **Advice:** The actual code that is executed at a join point. Different types of advice include:
   - **Before Advice:** Runs before a join point.
   - **After Advice:** Runs after a join point.
   - **Around Advice:** Runs both before and after the join point, allowing more control.
4. **Pointcut:** A set of join points where the advice should be applied. Pointcuts are typically defined using expressions to match specific join points in the code (e.g., all methods in a certain class).
5. **Weaving:** The process of linking aspects with other application code at specified join points. Weaving can occur at different times:
   - **Compile-time Weaving:** Aspects are woven into the code at compile time.
   - **Load-time Weaving:** Aspects are woven during class loading, after the code is compiled but before it is executed.
   - **Runtime Weaving:** Aspects are applied during program execution.
6. **Target Object:** The object whose method or behavior is being advised or intercepted by an aspect.

By using AOP, developers can modularize concerns that span multiple parts of an application, improving code readability, maintainability, and separation of concerns.
























