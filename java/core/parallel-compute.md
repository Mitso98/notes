# Parallel Programming in Java

Parallel programming is a type of computation in which many calculations or processes are carried out simultaneously. Large problems can often be divided into smaller ones, which can then be solved at the same time.

## Threading in Java

Java provides built-in support for multithreaded programming. A thread is a lightweight process that allows concurrent execution of two or more parts of a program.

### Creating Threads

There are two ways to create a thread in Java:
1. By extending the `Thread` class.
2. By implementing the `Runnable` interface.

#### Example: Extending the `Thread` Class

```java
public class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running...");
    }

    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();
    }
}
```

#### Example: Implementing the `Runnable` Interface

```java
public class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running...");
    }

    public static void main(String[] args) {
        Thread t1 = new Thread(new MyRunnable());
        t1.start();
    }
}
```

## Synchronization in Java

Synchronization is a mechanism that ensures that two or more concurrent threads do not simultaneously execute some particular program segment known as a critical section. This is necessary to prevent race conditions.

### Synchronized Methods

A synchronized method ensures that only one thread can execute it at a time for a given object.

```java
public class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}
```

### Synchronized Blocks

A synchronized block is used to lock an object for any shared resource.

```java
public class Counter {
    private int count = 0;

    public void increment() {
        synchronized (this) {
            count++;
        }
    }

    public int getCount() {
        return count;
    }
}
```

## Volatile Keyword

The `volatile` keyword in Java is used to indicate that a variable's value will be modified by different threads. It ensures that the value of the volatile variable is always read from the main memory and not from the thread's local cache.

```java
public class VolatileExample {
    private volatile boolean running = true;

    public void run() {
        while (running) {
            // Do something
        }
    }

    public void stop() {
        running = false;
    }
}
```

## Thread Communication

Java provides a way for threads to communicate with each other using `wait()`, `notify()`, and `notifyAll()` methods. These methods are part of the `Object` class and must be called within a synchronized context.

### wait()

The `wait()` method causes the current thread to wait until another thread invokes the `notify()` or `notifyAll()` method for the same object.

### notify()

The `notify()` method wakes up a single thread that is waiting on the object's monitor. If multiple threads are waiting, one of them is chosen to be awakened.

### notifyAll()

The `notifyAll()` method wakes up all threads that are waiting on the object's monitor.

### Example: Producer-Consumer Problem

```java
import java.util.LinkedList;
import java.util.Queue;

public class ProducerConsumer {
    private Queue<Integer> queue = new LinkedList<>();
    private final int LIMIT = 10;
    private final Object lock = new Object();

    public void produce() throws InterruptedException {
        int value = 0;
        while (true) {
            synchronized (lock) {
                while (queue.size() == LIMIT) {
                    lock.wait();
                }
                queue.add(value++);
                lock.notify();
            }
        }
    }

    public void consume() throws InterruptedException {
        while (true) {
            synchronized (lock) {
                while (queue.isEmpty()) {
                    lock.wait();
                }
                int value = queue.poll();
                System.out.println("Consumed: " + value);
                lock.notify();
            }
        }
    }

    public static void main(String[] args) throws InterruptedException {
        ProducerConsumer pc = new ProducerConsumer();
        Thread producerThread = new Thread(() -> {
            try {
                pc.produce();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        Thread consumerThread = new Thread(() -> {
            try {
                pc.consume();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        producerThread.start();
        consumerThread.start();

        producerThread.join();
        consumerThread.join();
    }
}
```

### Explanation of Producer-Consumer Example

- **Producer**: Continuously produces values and adds them to the queue. If the queue is full, it waits until a consumer consumes an item.
- **Consumer**: Continuously consumes values from the queue. If the queue is empty, it waits until a producer produces an item.
- **Synchronization**: The `synchronized` block ensures that only one thread can access the queue at a time.
- **wait() and notify()**: The `wait()` method is used to make the producer or consumer wait when the queue is full or empty, respectively. The `notify()` method is used to wake up the waiting thread when an item is added or removed from the queue.

## Conclusion

Parallel programming in Java involves using threads to perform concurrent tasks. Synchronization mechanisms such as synchronized methods, synchronized blocks, and the `volatile` keyword help manage access to shared resources and prevent race conditions. Thread communication can be achieved using `wait()`, `notify()`, and `notifyAll()` methods to coordinate the execution of threads.
