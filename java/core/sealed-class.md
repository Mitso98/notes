# Sealed Classes in Java

Sealed classes are a feature introduced in Java 15 as a preview feature and became a standard feature in Java 17. They provide more control over the inheritance hierarchy of classes. A sealed class restricts which other classes or interfaces may extend or implement it.

## Key Points

- **Declaration**: A class is declared as sealed using the `sealed` modifier.
- **Permitted Subclasses**: The subclasses that are allowed to extend the sealed class must be explicitly specified using the `permits` clause.
- **Final, Non-Sealed, and Sealed Subclasses**: The permitted subclasses can be declared as `final`, `non-sealed`, or `sealed`.

## Example

```java
public sealed class Shape permits Circle, Square, Rectangle {
    // ...existing code...
}

public final class Circle extends Shape {
    // ...existing code...
}

public sealed class Square extends Shape permits FilledSquare {
    // ...existing code...
}

public non-sealed class Rectangle extends Shape {
    // ...existing code...
}

public final class FilledSquare extends Square {
    // ...existing code...
}
```

In this example:
- `Shape` is a sealed class that permits `Circle`, `Square`, and `Rectangle` to extend it.
- `Circle` is a final class, meaning it cannot be subclassed.
- `Square` is a sealed class that permits only `FilledSquare` to extend it.
- `Rectangle` is a non-sealed class, meaning it can be subclassed by any other class.
- `FilledSquare` is a final class extending `Square`.

## Benefits

- **Enhanced Control**: Sealed classes provide better control over the class hierarchy, ensuring that only specific classes can extend a particular class.
- **Improved Security**: By restricting the subclasses, sealed classes can help in maintaining the integrity and security of the code.
- **Better Maintainability**: They make the code more maintainable by clearly defining the allowed subclasses.

## Use Cases

Sealed classes are particularly useful in scenarios where you want to have a fixed set of subclasses, such as:
- Defining a set of related types in a domain model.
- Creating a limited set of options for an API.
- Implementing algebraic data types.
