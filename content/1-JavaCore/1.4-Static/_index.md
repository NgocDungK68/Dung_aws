---
title : "Static"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 1.4 </b> "
---

<!-- ## Static in Java -->
![Static](/Dung_aws/images/1.4/0001.png)

#### What Are Static Elements?

- **Static elements** include variables and methods that belong to the class itself, rather than to any specific instance of the class. This means you can access static elements without creating an instance of the class.

## 1. Static Variables

- **Static variables** are shared among all instances of a class. Every instance of that class shares the same value for the static variable. Static variables are declared with the **static** keyword.

#### Declaring and Using Static Variables

- Static variables are declared inside the class with the **static** keyword. They can be accessed using the class name rather than an instance of the class.

    ```java
    class Counter {
        static int count = 0; // Static variable

        void increment() {
            count++;
        }
    }

    // Using static variable
    Counter c1 = new Counter();
    Counter c2 = new Counter();

    c1.increment();
    System.out.println(Counter.count); // Prints 1
    ```

#### Difference Between Static and Instance Variables

- **Static variables**: Belong to the class and are shared by all instances of the class.
- **Instance variables**: Belong to individual objects, with each object having its own copy.

#### When to Use Static Variables
Static variables are useful for storing values that are common to all instances of the class, such as a count of how many objects have been created.


## 2. Static Methods

#### What Are Static Methods?
Static methods are methods that belong to the class rather than to any specific instance of the class. They can be called using the class name, without needing to create an instance of the class.

#### Declaring and Using Static Methods:
Static methods are declared using the static keyword. Since they belong to the class, they cannot access instance variables or instance methods directly. Instead, they can only access other static variables and methods within the class.

```java
class MathUtil {
    static int square(int x) {
        return x * x;
    }
}

// Using static method
int result = MathUtil.square(5); // Calls the static method without creating an instance
System.out.println(result); // Prints 25
```
#### When to Use Static Methods:
Static methods are useful for utility or helper methods that perform operations that don’t require data from an instance of the class. For example, mathematical operations like Math.sqrt() or Math.pow() are implemented as static methods.

```java
class Example {
    static void displayMessage() {
        System.out.println("This is a static method.");
    }

    public static void main(String[] args) {
        Example.displayMessage(); // Calling the static method using the class name
    }
}
```


## 3. Static Blocks:
Static blocks are blocks of code that are executed once when the class is first loaded. They are used for initializing static variables or performing setup tasks that need to run once.

#### Declaring and Using Static Blocks:

A static block is declared inside the class with the **static** keyword and doesn’t return a value. It runs automatically when the class is loaded, before any instances are created.

```java
class Example {
    static {
        System.out.println("Static block executed");
    }
}
```

#### Initialization Order in Java:

When a class is loaded, the initialization happens in this order:
- Static fields (variables) are initialized.
- Static blocks are executed.
- Static Methods are executed only when called, and are not part of the automatic initialization process.


