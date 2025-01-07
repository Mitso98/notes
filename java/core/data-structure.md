# Data Structures in Java

## 1. Array
- **Description**: A collection of elements identified by index.
- **Complexity**:
  - Access: O(1)
  - Search: O(n)
  - Insertion: O(n)
  - Deletion: O(n)
- **When to Use**: When you need fast access to elements by index and the size of the collection is fixed.
- **When Not to Use**: When you need to frequently insert or delete elements, or when the size of the collection can change.
- **Real-Life Example**: Storing the daily temperatures of a week.

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
- **When to Use**: When you need a dynamic array that can grow and shrink in size, and you need fast access to elements by index.
- **When Not to Use**: When you need to frequently insert or delete elements in the middle of the list.
- **Real-Life Example**: Managing a list of students in a classroom where students can join or leave.

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
- **When to Use**: When you need to frequently insert or delete elements, especially at the beginning or end of the list.
- **When Not to Use**: When you need fast access to elements by index.
- **Real-Life Example**: Implementing a browser's back and forward navigation.

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
- **When to Use**: When you need fast access to key-value pairs and the order of elements is not important.
- **When Not to Use**: When you need to maintain the order of elements or need to frequently iterate over the keys in a specific order.
- **Real-Life Example**: Storing user information in a web application where each user has a unique ID.

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
- **When to Use**: When you need to manage a collection of elements with LIFO access, such as for undo functionality or parsing expressions.
- **When Not to Use**: When you need random access to elements or need to frequently iterate over the elements.
- **Real-Life Example**: Implementing undo functionality in text editors.

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
- **When to Use**: When you need to manage a collection of elements with FIFO access, such as for task scheduling or buffering.
- **When Not to Use**: When you need random access to elements or need to frequently iterate over the elements.
- **Real-Life Example**: Managing tasks in a printer queue.

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

## 7. HashSet
- **Description**: A hash table-based implementation of the Set interface.
- **Complexity**:
  - Access: O(1) (amortized)
  - Search: O(1) (amortized)
  - Insertion: O(1) (amortized)
  - Deletion: O(1) (amortized)
- **When to Use**: When you need a collection of unique elements with fast access.
- **When Not to Use**: When you need to maintain the order of elements.
- **Real-Life Example**: Storing a collection of unique user IDs.

#### Example:
```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<Integer> set = new HashSet<>();
        set.add(10);
        set.add(20);
        set.add(30);

        // Access element
        System.out.println("Set contains 20: " + set.contains(20));

        // Iterate over set
        for (Integer element : set) {
            System.out.println("Element: " + element);
        }

        // Remove element
        set.remove(20);
        System.out.println("After removal, set contains 20: " + set.contains(20));
    }
}
```

## 8. TreeMap
- **Description**: A Red-Black tree-based implementation of the NavigableMap interface.
- **Complexity**:
  - Access: O(log n)
  - Search: O(log n)
  - Insertion: O(log n)
  - Deletion: O(log n)
- **When to Use**: When you need a sorted map with fast access.
- **When Not to Use**: When you don't need the elements to be sorted.
- **Real-Life Example**: Storing a dictionary where keys are words and values are definitions.

#### Example:
```java
import java.util.TreeMap;

public class TreeMapExample {
    public static void main(String[] args) {
        TreeMap<String, Integer> map = new TreeMap<>();
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

## 9. ConcurrentHashMap
- **Description**: A thread-safe implementation of the Map interface.
- **Complexity**:
  - Access: O(1) (amortized)
  - Search: O(1) (amortized)
  - Insertion: O(1) (amortized)
  - Deletion: O(1) (amortized)
- **When to Use**: When you need a thread-safe map with fast access.
- **When Not to Use**: When thread safety is not a concern.
- **Real-Life Example**: Storing session data in a web application where multiple threads access the data concurrently.

#### Example:
```java
import java.util.concurrent.ConcurrentHashMap;

public class ConcurrentHashMapExample {
    public static void main(String[] args) {
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
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

## 10. Hash Table
- **Description**: A data structure that maps keys to values using a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.
- **Complexity**:
  - Access: O(1) (amortized)
  - Search: O(1) (amortized)
  - Insertion: O(1) (amortized)
  - Deletion: O(1) (amortized)
- **When to Use**: When you need fast access to key-value pairs and the order of elements is not important.
- **When Not to Use**: When you need to maintain the order of elements or need to frequently iterate over the keys in a specific order.
- **Real-Life Example**: Implementing a cache where you need quick access to frequently used data.

#### Example:
```java
import java.util.Hashtable;

public class HashTableExample {
    public static void main(String[] args) {
        Hashtable<String, Integer> table = new Hashtable<>();
        table.put("one", 1);
        table.put("two", 2);
        table.put("three", 3);

        // Access element
        System.out.println("Value for key 'two': " + table.get("two"));

        // Iterate over table
        for (String key : table.keySet()) {
            System.out.println("Key: " + key + ", Value: " + table.get(key));
        }

        // Remove element
        table.remove("two");
        System.out.println("After removal, value for key 'two': " + table.get("two"));
    }
}
```

These examples cover some of the most commonly used data structures in Java, along with their complexities, basic methods, guidelines on when to use or avoid them, and real-life use cases.
