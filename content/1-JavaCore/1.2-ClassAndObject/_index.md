---
title : "Class and Object"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 1.2 </b> "
---

## Basic concepts of Classes and Objects

#### Definition of Classes and Objects:

- **Class**: A class is a blueprint or template for creating objects. It defines attributes (variables) and methods (behaviors) that the objects created from the class will have. For example, a **Car** class might have attributes like **color**, **make**, and **model**, and methods like **start()**and **stop()**.

- **Object**: An object is a specific instance of a class. It is created based on the class and has specific values for its attributes. For instance, an object **myCar** of the **Car** class might have **color = "red"**, **make = "Toyota"**.


#### Declaring a class in Java
- A class is declared using the **class** keyword in Java, followed by the class name and curly braces **{}** enclosing the attributes and methods of the class.

```java
class Car {
    String color;
    String make;
    String model;

    void start() {
        System.out.println("Car started");
    }

    void stop() {
        System.out.println("Car stopped");
    }
}
```

#### Creating an Object from a Class
- An object is created from a class using the **new** keyword, followed by the class name and parentheses **()** to call the class's constructor.

```java
Car myCar = new Car(); // Create an object myCar from the Car class
```

- Once the object is created, you can access its attributes and methods.

```java
myCar.color = "red";  // Set the color attribute
myCar.start();        // Call the start() method
```


