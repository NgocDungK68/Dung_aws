---
title : "Attributes and Methods"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 1.3 </b> "
---

#### Concept of Attributes (Fields)
- **Attributes** are variables defined within a class that hold the state or properties of an object. Each object created from the class can have different values for these attributes.

- For example, a **Car** class might have attributes like **color**, **make**, and **model**.

#### Declaring Attributes

- Attributes are declared inside the class but outside any methods. They can have various access modifiers such as **private**, **protected**, or **public**.

```java
class Car {
    String color;
    String make;
    String model;
}
```

#### Concept of Methods
- A **method** is an action or function that a class can perform. Methods are used to operate on an object's attributes or perform specific tasks.
- For example, a **Car** class might have methods like **start()** to start the car and **stop()** to stop it.

#### Declaring and Calling Methods
- Methods are declared with a return type (or **void** if no value is returned), a name, and optionally parameters. Methods can be called on objects of the class to perform actions.

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

    void setColor(String newColor) {
        color = newColor;
    }
}
```
