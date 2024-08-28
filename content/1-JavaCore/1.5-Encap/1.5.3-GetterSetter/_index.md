---
title : "Getters and Setters"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 1.5.3 </b> "
---


Public methods used to access and modify the private fields of a class. They allow controlled access to the fields and can include validation logic.

```java
class Person {
    private String name; // Private field

    // Getter for the name field
    public String getName() {
        return name;
    }

    // Setter for the name field
    public void setName(String name) {
        this.name = name;
    }
}
```

#### Example of Encapsulation in Java:
When a field is declared private, it can only be accessed through public methods like getters and setters, ensuring that any changes to the field are validated and controlled.

```java
class Account {
    private double balance; // Private field

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
        }
    }
}
```

#### Summary:
Encapsulation is a fundamental technique in object-oriented programming that protects and manages data. It is achieved through the use of access modifiers and getter/setter methods, which provide controlled access to an object's internal state.





