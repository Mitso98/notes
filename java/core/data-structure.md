# Data Structures in Java

## 1. Array
- **Description**: A collection of elements identified by index.
- **Complexity**:
  - Access: O(1)
  - Search: O(n)
  - Insertion: O(n)
  - Deletion: O(n)

#### Example:
```java
public class ArrayExample {
    public static void main(String[] args) {
        int[] array = new int[5];
        array[0] = 10;
        array[1] = 20;
        array[2] = 30;
        array[3] = 40;
        array[4] = 50;

        // Access element
        System.out.println("Element at index 2: " + array[2]);

        // Iterate over array
        for (int i = 0; i < array.length; i++) {
            System.out.println("Element at index " + i + ": " + array[i]);
        }
    }
}
```

## 2. ArrayList
- **Description**: A resizable array implementation of the List interface.
- **Complexity**:
  - Access: O(1)
  - Search: O(n)
  - Insertion: O(n) (amortized O(1) if adding at the end)
  - Deletion: O(n)

#### Example:
```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        list.add(10);
        list.add(20);
        list.add(30);

        // Access element
        System.out.println("Element at index 1: " + list.get(1));

        // Iterate over list
        for (int i = 0; i < list.size(); i++) {
            System.out.println("Element at index " + i + ": " + list.get(i));
        }

        // Remove element
        list.remove(1);
        System.out.println("After removal, element at index 1: " + list.get(1));
    }
}
```

## 3. LinkedList
- **Description**: A doubly-linked list implementation of the List and Deque interfaces.
- **Complexity**:
  - Access: O(n)
  - Search: O(n)
  - Insertion: O(1)
  - Deletion: O(1)

#### Example:
```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        list.add(10);
        list.add(20);
        list.add(30);

        // Access element
        System.out.println("First element: " + list.getFirst());

        // Iterate over list
        for (int i = 0; i < list.size(); i++) {
            System.out.println("Element at index " + i + ": " + list.get(i));
        }

        // Remove element
        list.remove(1);
        System.out.println("After removal, element at index 1: " + list.get(1));
    }
}
```

## 4. HashMap
- **Description**: A hash table-based implementation of the Map interface.
- **Complexity**:
  - Access: O(1) (amortized)
  - Search: O(1) (amortized)
  - Insertion: O(1) (amortized)
  - Deletion: O(1) (amortized)

#### Example:
```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        HashMap<String, Integer> map = new HashMap<>();
        map.put("one", 1);
        map.put("two", 2);
        map.put("three", 3);

        // Access element
        System.out.println("Value for key 'two': " + map.get("two"));

        // Iterate over map
        for (String key : map.keySet()) {
            System.out.println("Key: " + key + ", Value: " + map.get(key));
        }

        // Remove element
        map.remove("two");
        System.out.println("After removal, value for key 'two': " + map.get("two"));
    }
}
```

## 5. Stack
- **Description**: A last-in, first-out (LIFO) stack of objects.
- **Complexity**:
  - Access: O(n)
  - Search: O(n)
  - Insertion: O(1)
  - Deletion: O(1)

#### Example:
```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(10);
        stack.push(20);
        stack.push(30);

        // Access element
        System.out.println("Top element: " + stack.peek());

        // Iterate over stack
        while (!stack.isEmpty()) {
            System.out.println("Popped element: " + stack.pop());
        }
    }
}
```

## 6. Queue
- **Description**: A first-in, first-out (FIFO) queue of objects.
- **Complexity**:
  - Access: O(n)
  - Search: O(n)
  - Insertion: O(1)
  - Deletion: O(1)

#### Example:
```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();
        queue.add(10);
        queue.add(20);
        queue.add(30);

        // Access element
        System.out.println("Front element: " + queue.peek());

        // Iterate over queue
        while (!queue.isEmpty()) {
            System.out.println("Removed element: " + queue.poll());
        }
    }
}
```

These examples cover some of the most commonly used data structures in Java, along with their complexities and basic methods.
