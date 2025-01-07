# Java Stream API

The Stream API, introduced in Java 8, is a powerful feature that allows for functional-style operations on streams of elements. It provides a way to process collections of objects in a declarative manner.

## Key Concepts

### Stream
A sequence of elements supporting sequential and parallel aggregate operations. Streams are not data structures; they do not store elements. Instead, they convey elements from a source such as a data structure, an array, or an I/O channel, through a pipeline of computational operations.

### Intermediate Operations
Operations that transform a stream into another stream. They are always lazy, meaning they do not execute until a terminal operation is invoked. Examples include `filter()`, `map()`, and `sorted()`.

### Terminal Operations
Operations that produce a result or a side-effect, such as `forEach()`, `collect()`, and `reduce()`. Terminal operations trigger the processing of the stream pipeline.

## Creating Streams
Streams can be created from various data sources, such as collections, arrays, or I/O channels.

```java
List<String> myList = Arrays.asList("a", "b", "c", "d");
Stream<String> stream = myList.stream();
```

## Common Operations

### Filtering
Filters elements based on a predicate.

```java
List<String> filtered = myList.stream()
    .filter(s -> s.startsWith("a"))
    .collect(Collectors.toList());
```

### Mapping
Transforms each element using a function.

```java
List<String> upperCaseList = myList.stream()
    .map(String::toUpperCase)
    .collect(Collectors.toList());
```

### Reducing
Combines elements to produce a single result.

```java
int sum = Arrays.asList(1, 2, 3, 4).stream()
    .reduce(0, Integer::sum);
```

### Collecting
Collects the elements of the stream into a collection.

```java
List<String> list = myList.stream()
    .collect(Collectors.toList());
```

### Sorting
Sorts the elements of the stream.

```java
List<String> sortedList = myList.stream()
    .sorted()
    .collect(Collectors.toList());
```

### Distinct
Removes duplicate elements from the stream.

```java
List<String> distinctList = myList.stream()
    .distinct()
    .collect(Collectors.toList());
```

### Limit
Limits the number of elements in the stream.

```java
List<String> limitedList = myList.stream()
    .limit(2)
    .collect(Collectors.toList());
```

### Skip
Skips the first N elements of the stream.

```java
List<String> skippedList = myList.stream()
    .skip(2)
    .collect(Collectors.toList());
```

### FlatMap
Flattens nested structures.

```java
List<Integer> flatMappedList = Arrays.asList(Arrays.asList(1, 2), Arrays.asList(3, 4)).stream()
    .flatMap(List::stream)
    .collect(Collectors.toList());
```

### Peek
Performs an action for each element of the stream.

```java
myList.stream()
    .peek(System.out::println)
    .collect(Collectors.toList());
```

### Match
Checks if elements match a given predicate.

```java
boolean anyMatch = myList.stream()
    .anyMatch(s -> s.startsWith("a"));

boolean allMatch = myList.stream()
    .allMatch(s -> s.length() == 1);

boolean noneMatch = myList.stream()
    .noneMatch(s -> s.isEmpty());
```

### Find
Finds elements in the stream.

```java
Optional<String> first = myList.stream()
    .findFirst();

Optional<String> any = myList.stream()
    .findAny();
```

### Count
Counts the number of elements in the stream.

```java
long count = myList.stream()
    .count();
```

## Parallel Streams
Streams can be processed in parallel to leverage multi-core architectures.

```java
List<String> parallelFiltered = myList.parallelStream()
    .filter(s -> s.startsWith("a"))
    .collect(Collectors.toList());
```

## Conclusion
The Stream API provides a powerful and flexible way to process collections of data in Java. By using streams, you can write more concise and readable code that is also potentially more efficient when using parallel streams.
