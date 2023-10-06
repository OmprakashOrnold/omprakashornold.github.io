
## 1) Singleton Design Pattern

## 2) How HashMap works internally

## 3) Fail safe and fail fast collections

| Feature | Fail-Safe Collections | Fail-Fast Collections |
| --- | --- | --- |
| Concurrent Modification | Does not throw `ConcurrentModificationException` when modifying the collection while iterating | Throws `ConcurrentModificationException` when modifying the collection while iterating |
| Iteration | Iterates over a copy of the collection to avoid concurrent modification | Iterates over the original collection |
| Thread-Safety | Provides weak consistency and thread-safety by using a copy of the collection | Provides stronger consistency and no thread-safety by using the original collection |
| Examples | `CopyOnWriteArrayList`, `ConcurrentHashMap` | `ArrayList`, `HashMap`, `HashSet` |

Here are some syntax examples:

```java
// Fail-Safe Collections
CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();

// Fail-Fast Collections
ArrayList<String> list = new ArrayList<>();
HashMap<String, Integer> map = new HashMap<>();
HashSet<String> set = new HashSet<>();
``` 

Note that the choice of which type of collection to use depends on the specific requirements of the application, as both fail-safe and fail-fast collections have their own advantages and disadvantages.

## 4) What is Constructor Chaining

## 5) What are the methods available in Object class?
The `Object` class is a fundamental class in Java that is the parent class of all other classes. It provides a set of common methods that can be used by all Java objects. Here are some of the most commonly used methods in the `Object` class:

1. `toString()`: This method returns a string representation of the object.

2. `equals(Object obj)`: This method compares the current object with another object to determine if they are equal.

3. `hashCode()`: This method returns a hash code value for the object.

4. `getClass()`: This method returns the class object associated with the object.

5. `wait()`: This method causes the current thread to wait until another thread calls the `notify()` or `notifyAll()` method.

6. `notify()`: This method wakes up a single thread that is waiting on the object's monitor.

7. `notifyAll()`: This method wakes up all threads that are waiting on the object's monitor.

8. `finalize()`: This method is called by the garbage collector before the object is destroyed.

9. `clone()`: This method creates a new object that is a copy of the current object.

10. `getClassLoader()`: This method returns the class loader for the class.

11. `finalize()`: This method is called by the garbage collector before the object is destroyed.

These are just a few examples of the many methods available in the `Object` class. All these methods are public and can be overridden by the subclasses to provide their own implementation.

## 6) How many ways we can create Object for class in java ?
There are four ways to create an object for a class in Java:

1. Using the `new` keyword: This is the most common way to create an object in Java. We use the `new` keyword followed by the class name and a set of parentheses to create a new object of that class. For example:

   `````java
   MyClass obj = new MyClass();
   ```

2. Using `newInstance()` method: We can use the `newInstance()` method of the `Class` class to create a new instance of the class. This method creates an object of the class and initializes it with the default constructor (i.e., the constructor that takes no arguments). For example:

   ````java
   MyClass obj = MyClass.class.newInstance();
   ```

   Note that this method is deprecated in Java 9 and removed in Java 11.

3. Using `clone()` method: We can use the `clone()` method to create a new object that is a copy of an existing object. The class must implement the `Cloneable` interface to use this method. For example:

   ````java
   MyClass obj1 = new MyClass();
   MyClass obj2 = obj1.clone();
   ```

4. Using deserialization: We can create an object by deserializing it from a stream. The class must implement the `Serializable` interface to enable serialization and deserialization. For example:

   ````java
   // Serialization
   ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("file.txt"));
   out.writeObject(obj);
   out.close();

   // Deserialization
   ObjectInputStream in = new ObjectInputStream(new FileInputStream("file.txt"));
   MyClass obj = (MyClass) in.readObject();
   in.close();
   ```

These are the four ways to create an object for a class in Java. Note that the first method (using the `new` keyword) is the most commonly used and recommended way to create objects in Java.

## 7) What is Cloning and why we need it ?

   Cloning in Java refers to the process of creating an exact copy of an object.In other words, it allows you to duplicate an object, producing a new object with the same state as the original one
   Java provides cloning support through the Cloneable interface and the clone() method.
   
  - Cloneable interface:
        The Cloneable interface acts as a marker interface 
  - clone() method:
        The clone() method is defined in the Object class, 

## 8) String vs StringBuffer vs StringBuilder
   | Feature        | String           | StringBuffer  | StringBuilder  |
| ------------- |-------------| -----| -----|
| Mutability      | Immutable (cannot be changed) | Mutable (can be changed) | Mutable (can be changed) |
| Thread-safe     | Yes (immutable) | Yes (synchronized) | (not synchronized) |
| Performance     | Slower due to creating new objects when modified | Faster than String for concatenation/modification | Faster than String for concatenation/modification |
| Memory usage    | Creates a new object every time it is modified | Modifies the existing object without creating new ones | Modifies the existing object without creating new ones |

## 9) What is Exception Hierarchy in Java ?

- **java.lang.Object**
  - **java.lang.Throwable**
    - **java.lang.Error**: Represents serious errors that are beyond the application's control and typically not recoverable. Examples include `OutOfMemoryError` and `StackOverflowError`.
    - **java.lang.Exception**: Represents exceptional conditions that might be caught and handled by the application. It is further divided into:
      - **java.lang.RuntimeException**: Represents exceptions that occur at runtime and are unchecked, meaning they do not need to be declared in the method's throws clause. Common subclasses include:
        - **java.lang.NullPointerException**: Occurs when trying to access an object or call a method on a null reference.
        - **java.lang.ArithmeticException**: Occurs when arithmetic operations result in an error, such as division by zero.
        - **java.lang.IndexOutOfBoundsException**: Occurs when trying to access an invalid index in an array, string, or collection.
        - ... (and more)
      - **java.lang.Exception**: Represents exceptions that are checked, meaning they must be either caught using try-catch blocks or declared in the method's throws clause. Common subclasses include:
        - **java.io.IOException**: Represents exceptions related to input-output operations, such as reading/writing files.
        - **java.sql.SQLException**: Represents exceptions related to database access.
        - **java.lang.InterruptedException**: Occurs when a thread is interrupted.
        - ... (and more)


## 10) What is Serialization and De-Serialization ?

#### Serialization 
 - It is the process of converting an object into a format that can be easily stored, transmitted, or reconstructed later.
 - It involves converting the object's state (its data and structure) into a byte stream or another suitable format.
 - This serialized representation can then be saved to a file, sent over a network, or stored in a database.

### Example
```java 
Person person = new Person("John Doe", 30, "123 Main St");
```

```java
try {
    FileOutputStream fileOut = new FileOutputStream("person.ser");
    ObjectOutputStream out = new ObjectOutputStream(fileOut);
    out.writeObject(person);
    out.close();
    fileOut.close();
    System.out.println("Serialized data saved in person.ser");
} catch (IOException e) {
    e.printStackTrace();
}

```

#### De-serialization
on the other hand, is the reverse process of serialization.

```java 
Person person = new Person("John Doe", 30, "123 Main St");
```


```java
try {
    FileInputStream fileIn = new FileInputStream("person.ser");
    ObjectInputStream in = new ObjectInputStream(fileIn);
    Person deserializedPerson = (Person) in.readObject();
    in.close();
    fileIn.close();
    System.out.println("Deserialized data: " + deserializedPerson.toString());
} catch (IOException | ClassNotFoundException e) {
    e.printStackTrace();

```

### Example

## 11) What is transient keyword in java ?

## 12) Diff between Comparable and Comparator
| Feature      | Comparable                  | Comparator                   |
|--------------|-----------------------------|------------------------------|
| Purpose      | Natural ordering for objects| Custom sorting for objects   |
| Interface    | Comparable                  | Comparator                   |
| Method       | `compareTo()`               | `compare()`                  |
| Usage        | `Collections.sort(list)`    | `Collections.sort(list, comparator)` or other sorting methods |
| Example      | See code example below      | See code example below       |


#### Example of Comparable:

```java
public class Person implements Comparable<Person> {
    private String name;
    private int age;

    // constructor and other methods

    @Override
    public int compareTo(Person otherPerson) {
        // Compare based on age for this example
        return this.age - otherPerson.age;
    }
}

```

#### Example of Comparator:

```java
public class PersonNameComparator implements Comparator<Person> {
    @Override
    public int compare(Person person1, Person person2) {
        // Compare based on names for this example
        return person1.getName().compareTo(person2.getName());
    }
}
```

## 13) How many ways we can create Thread in java ?
There are two ways to create threads in Java:

#### 1. Extending the Thread class:
``` java
class MyThread extends Thread {
  public void run() {
    // Code to be executed in this thread
  }
}

// Creating and starting the thread
MyThread thread = new MyThread();
thread.start();
```

#### 2. Implementing the Runnable interface:
``` java
class MyRunnable implements Runnable {
  public void run() {
    // Code to be executed in this thread
  }
}

// Creating and starting the thread
MyRunnable runnable = new MyRunnable();
Thread thread = new Thread(runnable);
thread.start();
```
In both cases, the code to be executed in the thread is written inside the `run()` method. The `start()` method is used to start the thread and execute the `run()` method in a separate thread of execution.
## 14) Runnable vs Callable in Java

Here's a table outlining the main differences between `Runnable` and `Callable` interfaces in Java:

|            | `Runnable` | `Callable` |
|------------|------------|------------|
| Interface definition | `public interface Runnable { void run(); }` | `public interface Callable<V> { V call() throws Exception; }` |
| Return value | `void` | `V` |
| Throwing checked exceptions | Cannot throw checked exceptions | Can throw checked exceptions |
| Usage with threads | Can be used to create threads, but cannot return a value or throw checked exceptions | Can be used to create threads and return a value or throw checked exceptions |
| Usage with `ExecutorService` | Can be submitted to an `ExecutorService`, which returns a `Future<?>` object | Can be submitted to an `ExecutorService`, which returns a `Future<V>` object |

In summary, `Runnable` is a simpler interface that can be used to define a task that can be executed in a separate thread, but it cannot return a value or throw checked exceptions. On the other hand, `Callable` is a more flexible interface that can be used to define a task that can be executed in a separate thread and return a value or throw checked exceptions. `Callable` is typically used with an `ExecutorService` to submit tasks and obtain the results through `Future` objects.

```java
import java.util.concurrent.*;

public class ThreadExample {
    
    public static void main(String[] args) throws InterruptedException, ExecutionException {
        
        // Creating a thread using Runnable interface
        Runnable runnableTask = () -> {
            System.out.println("This is a Runnable task");
        };
        Thread thread1 = new Thread(runnableTask);
        thread1.start();

        // Creating a thread using Callable interface
        Callable<Integer> callableTask = () -> {
            System.out.println("This is a Callable task");
            return 42;
        };
        ExecutorService executorService = Executors.newSingleThreadExecutor();
        Future<Integer> future = executorService.submit(callableTask);
        Integer result = future.get();
        System.out.println("Result from Callable task: " + result);
        executorService.shutdown();
    }
}
```
## 15) What is Executor Framework in Java

## 16) What is the contract between hashCode ( ) & equals ( ) methods

## 17) Checked Vs Unchecked exception
here's a table summarizing the key differences between checked and unchecked exceptions in Java, along with their syntax examples:

| Feature | Checked Exceptions | Unchecked Exceptions |
| --- | --- | --- |
| Handling | Must be handled by the calling method or declared in the method signature | Can be handled by the calling method or left to propagate up the call stack |
| Syntax | Declared with the `throws` keyword in method signature | Extends `RuntimeException` class or one of its subclasses |
| Examples | `IOException`, `SQLException` | `NullPointerException`, `ArrayIndexOutOfBoundsException` |

Here are some syntax examples:

```java
// Checked Exceptions
public void readFromFile(String filename) throws IOException {
    // code that reads from a file
}

public void executeQuery(String query) throws SQLException {
    // code that executes a database query
}

// Unchecked Exceptions
public void printArray(int[] arr) {
    for (int i = 0; i <= arr.length; i++) {
        System.out.println(arr[i]);
    }
}

public void divide(int a, int b) {
    int result = a / b;
}
```

Note that the choice of whether to use a checked or unchecked exception depends on the specific requirements of the application. In general, it is recommended to use checked exceptions for recoverable errors that can be handled by the calling method, and unchecked exceptions for unrecoverable errors that should propagate up the call stack.

## 18) What is try-with-resources in java
Try-with-resources is a feature in Java that allows for automatic resource management. It is used to ensure that resources such as files, connections, and locks are properly closed and released, even if an exception is thrown.

Here is a real-time example of how try-with-resources works:

Suppose you are writing a program that reads data from a file and processes it. You want to make sure that the file is properly closed, regardless of whether an exception is thrown or not. You can use try-with-resources to achieve this.

Here is an example code snippet:
```
try (FileInputStream fis = new FileInputStream("file.txt")) {
    // read data from the file
}
```
In this example, the `FileInputStream` object is created inside the try block, and the `try` block is followed by a `(` character. This indicates that the resource (in this case, the file input stream) should be closed automatically when the try block is exited.

If an exception is thrown inside the try block, the resource will still be closed automatically, ensuring that the file is properly closed and released.

If no exception is thrown, the resource will be closed automatically when the try block is exited.

In summary, try-with-resources ensures that resources are properly closed and released, even if an exception is thrown, and it helps to avoid resource leaks in Java programs.

## 19) What are concurrent collections in java ?

Concurrent collections are a set of thread-safe collections in Java that allow multiple threads to access and modify them concurrently without the need for explicit synchronization. Here are some examples of concurrent collections in Java:

1. `ConcurrentHashMap`: A thread-safe implementation of the `Map` interface that allows multiple threads to access and modify the map concurrently. It is designed to be highly scalable and can be used in high-concurrency applications.

2. `ConcurrentSkipListMap`: A thread-safe implementation of the `NavigableMap` interface that allows multiple threads to access and modify the map concurrently. It is designed to be sorted and can be used in applications that require sorted maps.

3. `ConcurrentLinkedQueue`: A thread-safe implementation of the `Queue` interface that allows multiple threads to access and modify the queue concurrently. It is designed to be highly scalable and can be used in high-concurrency applications that require a queue.

4. `ConcurrentLinkedDeque`: A thread-safe implementation of the `Deque` interface that allows multiple threads to access and modify the deque concurrently. It is designed to be highly scalable and can be used in high-concurrency applications that require a deque.

5. `CopyOnWriteArrayList`: A thread-safe implementation of the `List` interface that allows multiple threads to access and modify the list concurrently. It is designed to be highly scalable and can be used in applications that require a list.

6. `CopyOnWriteArraySet`: A thread-safe implementation of the `Set` interface that allows multiple threads to access and modify the set concurrently. It is designed to be highly scalable and can be used in applications that require a set.

These are some examples of concurrent collections in Java. Note that these collections are designed to be thread-safe and can be used in concurrent applications. However, it is important to choose the right collection based on the specific requirements of the application.****

## 20) Difference between Interfaces & Abstract classes
Here is a comparison between interfaces and abstract classes in table format:

|Interfaces|Abstract Classes| 
|--|--|
|Interfaces define only method signatures, no method bodies.|Abstract classes can have implemented methods along with abstract methods.|
|Interfaces cannot have variables, they must be constants.|Abstract classes can have variables and constants.|    
|A class can implement multiple interfaces.|A class can only extend one abstract class but implement multiple interfaces.|
|Interfaces are useful when completely abstracting the behaviors of unrelated classes.|Abstract classes are useful for providing partially implemented functionality to related classes.| 
|Methods in interfaces are public by default.|Methods in abstract classes can have any access modifier.|
|Interfaces can only inherit other interfaces.|Abstract classes can inherit both abstract classes and interfaces.|
|Interfaces are ideal for defining contracts and rules.|Abstract classes are useful for functionality sharing among descendants.|

In short:
- Interfaces define contracts and rules that unrelated classes can implement 
- Abstract classes define default functionality that related classes can extend 


## 21) What is Shallow Cloning & Deep Cloning ?

## 22) What is the diff between filter ( ) and map ( ) methods in Stream API?
 here's a table summarizing the differences between the `filter()` and `map()` methods in Java Stream API:

| Method | Purpose | Return Type | Description |
| --- | --- | --- | --- |
| `filter()` | Filters the elements of a stream, returning a new stream containing only the elements that match the given predicate. | Stream | Returns a stream of elements that satisfy the given predicate. |
| `map()` | Maps the elements of a stream, returning a new stream containing elements that have been transformed in some way. | Stream | Returns a stream of elements that have been transformed using the provided mapping function. |

Here's a simple example to demonstrate the difference:
```
// Filter example
Stream.of(1, 2, 3, 4, 5)
    .filter(n -> n % 2 == 0)
    .forEach(System.out::println);
// Output: 2, 4

// Map example
Stream.of(1, 2, 3, 4, 5)
    .map(n -> n * 2)
    .forEach(System.out::println);
// Output: 2, 4, 6, 8, 10
```
In the filter example, the stream is filtered to only contain elements that satisfy the predicate `n % 2 == 0`, which means that only the even numbers 2 and 4 are printed.

In the map example, the stream is mapped to contain elements that have been transformed by multiplying each number by 2. This means that the resulting stream contains the original numbers multiplied by 2 (i.e., 2, 4, 6, 8, 10).

In summary, `filter()` is used to filter out elements that don't match a certain condition, while `map()` is used to transform elements in a stream.

## 23) What is the purpose of User Defined Exceptions ?

## 24) What is Factory Design Pattern ?

## 25) What is diff between ConcurrentHashMap and HashMap ?
Sure, here's a table that summarizes the key differences between `ConcurrentHashMap` and `HashMap` in Java:

| Feature | `ConcurrentHashMap` | `HashMap` |
| --- | --- | --- |
| Thread-safety | Thread-safe | Not thread-safe |
| Synchronization | Uses finer-grained locking for better concurrency | Uses a single lock for the entire table |
| Performance | Lower performance than `HashMap` in single-threaded environments, but scales better in highly concurrent environments | Higher performance than `ConcurrentHashMap` in single-threaded environments, but does not scale well in highly concurrent environments |
| Iteration | Supports safe concurrent iteration using a snapshot of the map | Does not support safe concurrent iteration |
| Null keys and values | Does not allow null keys or values | Allows null keys and values |
| Fail-safe iterators | Returns fail-safe iterators that do not throw `ConcurrentModificationException` | Returns fail-fast iterators that throw `ConcurrentModificationException` if the map is modified during iteration |
| Example | `java.util.concurrent.ConcurrentHashMap` | `java.util.HashMap` |

Here's a brief explanation of each feature:

1. Thread-safety: `ConcurrentHashMap` is thread-safe, while `HashMap` is not.

2. Synchronization: `ConcurrentHashMap` uses finer-grained locking for better concurrency, while `HashMap` uses a single lock for the entire table.

3. Performance: `ConcurrentHashMap` has lower performance than `HashMap` in single-threaded environments, but scales better in highly concurrent environments. `HashMap` has higher performance than `ConcurrentHashMap` in single-threaded environments, but does not scale well in highly concurrent environments.

4. Iteration: `ConcurrentHashMap` supports safe concurrent iteration using a snapshot of the map, while `HashMap` does not support safe concurrent iteration.

5. Null keys and values: `ConcurrentHashMap` does not allow null keys or values, while `HashMap` allows null keys and values.

6. Fail-safe iterators: `ConcurrentHashMap` returns fail-safe iterators that do not throw `ConcurrentModificationException`, while `HashMap` returns fail-fast iterators that throw `ConcurrentModificationException` if the map is modified during iteration.

Note that the choice of `ConcurrentHashMap` or `HashMap` depends on the specific requirements of the application. In general, `ConcurrentHashMap` is recommended for highly concurrent environments where thread-safety is critical, while `HashMap` is recommended for single-threaded environments where performance is a top priority.

## 26) What is Weak Hash Map in Java ?

## 27) How to read File Data using Java 8?

## 28) Program to generate Random Text using Java 

## 29) Program to generate OTP using Java

## 30) Program to check String contains only alphabets or not


## 31) What are the rules for Method Overrinding ?

## 32) What are variable arguments in Java ?

## 33) How to increase heap size while running java program ?

## 34) What are Generics in java ?

## 35) What is Auto Boxing and Auto Un-boxing ?

## 36) How to catch multiple exceptions using single catch block ?

## 37) What is StringJoiner class ?

## 38) What is SplIterator ?

## 39) Can we declare method as abstract and final ?
No, we cannot declare a method as both `abstract` and `final` in Java, as they are mutually exclusive modifiers.

The `abstract` modifier is used to define methods that have no implementation and must be implemented by the subclass. The `final` modifier, on the other hand, is used to define methods that cannot be overridden by the subclass.

If a method is declared as `abstract`, it means that the method is incomplete and must be implemented by the subclass. But if the same method is declared as `final`, it means that the method cannot be overridden, which contradicts the purpose of the `abstract` modifier.

Here's an example of how the combination of `abstract` and `final` modifiers would produce a compilation error:

```java
public abstract class MyClass {
    public abstract final void myMethod(); // Compilation error: illegal combination of modifiers
}
```

Note that it is possible to declare a class as both `abstract` and `final`, but this combination is rare and has a specific use case. When a class is declared as `abstract` and `final`, it means that the class cannot be instantiated and cannot be subclassed. An example of such a class is the `java.lang.Math` class, which contains a set of static methods and cannot be instantiated or subclassed.

## 40) How to create user defined Immutable classes in Java ?


## 41) How to sort 0's and 1's in given array

		Input : {1,0,1,0,0,1,1}
		Output : {0,0,0,1,1,1,1}

## 42) How to filter employees based on given salary using stream api

## 43) What is the difference between Lambda Expression & Method References

## 44) What is the use of default and static methods in interface

## 45) What is Optional class in java 8 ?

## 46) What is Completable Feature in Java ?

## 46) What are the class loaders available in Java ?

## 47) What is Thread Local class ?

## 48) Can we overload main ( ) method in java class ?

Yes, we can overload the `main()` method in a Java class. Here are the main points to consider:

- Overloading is a feature in Java that allows a class to have multiple methods with the same name but different parameters. 
- We can apply the same concept to the `main()` method and create multiple `main()` methods with different parameter lists.
- However, only the `main()` method with the standard signature (i.e., `public static void main(String[] args)`) can serve as the entry point of the program.
- If we define an overloaded `main()` method with a different signature, it can be called like any other method, but it will not be executed when we run the program.
- When we run a Java program, the JVM looks for the `main()` method with the standard signature and executes its code.
- If we want to call an overloaded `main()` method from the standard `main()` method, we can do so by passing appropriate arguments to the overloaded method.
- However, this is not a common practice and should only be used in specific scenarios where it makes sense to do so.
- In general, it is recommended to keep the `main()` method as simple as possible and delegate the actual work to other methods in the class.

## 49) Can we run java program without main ( ) method ?

Here are the main points to consider about running a Java program without a `main()` method:

- No, we cannot run a Java program without a `main()` method.
- The `main()` method is a special method that is the entry point of a Java program.
- The JVM (Java Virtual Machine) looks for the `main()` method and executes its code when we run a Java program.
- If a Java program does not have a `main()` method, the JVM will not be able to execute the program and will throw a runtime error.
- The `main()` method must be declared as `public`, `static`, and `void`, with a single parameter of type `String[]` (or `String...`).
- This is a requirement of the Java language specification.
- While other methods can be executed in a Java program and can perform various tasks, they cannot serve as the entry point for the program.
- The `main()` method is the only method that can be used as the entry point for a Java program.

## 50) What is Polymorphism explain with example ?

-  Exhibiting multiple behaviours based on situation is called as polymorphism

```java
public class PolymorphismExample {
    public static void main(String[] args) {
        Shape[] shapes = new Shape[3];
        shapes[0] = new Circle(5);
        shapes[1] = new Square(10);
        shapes[2] = new Triangle(3, 4, 5);

        for (Shape shape : shapes) {
            System.out.println("Area of " + shape.getClass().getSimpleName() + ": " + shape.getArea());
        }
    }
}

interface Shape {
    double getArea();
}

class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double getArea() {
        return Math.PI * radius * radius;
    }
}

class Square implements Shape {
    private double side;

    public Square(double side) {
        this.side = side;
    }

    public double getArea() {
        return side * side;
    }
}

class Triangle implements Shape {
    private double a;
    private double b;
    private double c;

    public Triangle(double a, double b, double c) {
        this.a = a;
        this.b = b;
        this.c = c;
    }

    public double getArea() {
        double s = (a + b + c) / 2;
        return Math.sqrt(s * (s - a) * (s - b) * (s - c));
    }
}
```

## 51) What are SOLID oops principles ?

## 52) What is Encapsulation with Example ?
 - Thre Process of combining data members and methods in single unit called encapsulaion

#### Encapsulation Exanple
```java
public class BankAccount {
    private double balance;

    public BankAccount(double balance) {
        this.balance = balance;
    }

    public void deposit(double amount) {
        balance += amount;
    }

    public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
        } else {
            System.out.println("Insufficient balance");
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

































