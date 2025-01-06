# String Literals, `new String()`, `StringBuilder`, and `StringBuffer` in Java

## String Literals

String literals are created by using double quotes. For example:
```java
String str = "Hello";
```
String literals are stored in a common pool called the string pool, which is a part of the Java heap memory. Internally, the string pool uses a HashMap to store the string literals. If a string literal already exists in the pool, a reference to the existing string is returned instead of creating a new object. This helps in saving memory.

## `new String()`

When you create a string using the `new` keyword, a new object is created in the heap memory, even if an equivalent string exists in the string pool. For example:
```java
String str = new String("Hello");
```
This approach is less memory efficient compared to string literals because it always creates a new object.

## `StringBuilder`

`StringBuilder` is a mutable sequence of characters. It is used when you need to modify a string frequently. It does not create new objects for each modification, which makes it more memory efficient and faster for modifications. For example:
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
```
`StringBuilder` uses a resizable array data structure to store the characters. It is not synchronized, which means it is not thread-safe but performs better in single-threaded environments.

## `StringBuffer`

`StringBuffer` is similar to `StringBuilder` but is synchronized, making it thread-safe. It is used when you need to modify a string in a multi-threaded environment. For example:
```java
StringBuffer sb = new StringBuffer("Hello");
sb.append(" World");
```
`StringBuffer` also uses a resizable array data structure to store the characters. Due to synchronization, `StringBuffer` is slower than `StringBuilder`.

## Which is Better for Modification?

- For single-threaded environments, `StringBuilder` is preferred due to its better performance.
- For multi-threaded environments, `StringBuffer` is preferred due to its thread-safety.
- For simple string assignments and minimal modifications, string literals are preferred for their memory efficiency.
