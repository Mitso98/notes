# Optional Class in Java

The `Optional` class in Java is a container object which may or may not contain a non-null value. It is a part of the `java.util` package and was introduced in Java 8. The primary purpose of the `Optional` class is to provide a type-level solution for representing optional values instead of using `null` references.

## Key Features

- **Avoid NullPointerException**: By using `Optional`, you can avoid `NullPointerException` by explicitly checking for the presence of a value.
- **Expressive Code**: It makes the code more readable and expressive by clearly indicating that a value may be absent.
- **Functional Programming**: `Optional` supports functional-style operations such as `map`, `flatMap`, `filter`, etc.

## Creating Optional Instances

You can create an `Optional` instance in several ways:

- **Empty Optional**: Represents no value.
  ```java
  Optional<String> emptyOptional = Optional.empty();
  ```

- **Non-Empty Optional**: Contains a non-null value.
  ```java
  Optional<String> nonEmptyOptional = Optional.of("Hello");
  ```

- **Nullable Optional**: Can contain a null value.
  ```java
  Optional<String> nullableOptional = Optional.ofNullable(null);
  ```

## Common Methods

- **isPresent()**: Checks if there is a value present.
  ```java
  if (optional.isPresent()) {
      // Value is present
  }
  ```

- **ifPresent()**: Executes a block of code if a value is present.
  ```java
  optional.ifPresent(value -> System.out.println(value));
  ```

- **orElse()**: Returns the value if present, otherwise returns a default value.
  ```java
  String value = optional.orElse("Default Value");
  ```

- **orElseGet()**: Returns the value if present, otherwise invokes a supplier and returns the result.
  ```java
  String value = optional.orElseGet(() -> "Default Value");
  ```

- **orElseThrow()**: Returns the value if present, otherwise throws an exception.
  ```java
  String value = optional.orElseThrow(() -> new IllegalArgumentException("Value not present"));
  ```

- **map()**: Transforms the value if present.
  ```java
  Optional<Integer> length = optional.map(String::length);
  ```

- **flatMap()**: Similar to `map`, but the mapping function returns an `Optional`.
  ```java
  Optional<Integer> length = optional.flatMap(value -> Optional.of(value.length()));
  ```

- **filter()**: Returns an `Optional` describing the value if it matches a predicate.
  ```java
  Optional<String> filtered = optional.filter(value -> value.startsWith("H"));
  ```

## Example Usage

Here is an example demonstrating the usage of `Optional`:

```java
public class OptionalExample {
    public static void main(String[] args) {
        Optional<String> optional = Optional.of("Hello, World!");

        // Check if value is present
        if (optional.isPresent()) {
            System.out.println("Value is present: " + optional.get());
        }

        // Use ifPresent to execute a block of code
        optional.ifPresent(value -> System.out.println("Value: " + value));

        // Use orElse to provide a default value
        String defaultValue = optional.orElse("Default Value");
        System.out.println("Default Value: " + defaultValue);

        // Use map to transform the value
        Optional<Integer> length = optional.map(String::length);
        length.ifPresent(len -> System.out.println("Length: " + len));
    }
}
```

The `Optional` class is a powerful tool for handling optional values in Java, making your code more robust and less prone to `NullPointerException`.
