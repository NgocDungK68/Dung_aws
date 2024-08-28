---
title : "Concept of Inheritance"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.7.1 </b> "
---

#### What is Inheritance?
- **Inheritance** is a core feature of object-oriented programming that allows one class (subclass) to inherit attributes and methods from another class (superclass).
- This enables code reuse and extension of the superclass functionality without rewriting code.

#### Benefits of Inheritance:
- **Code Reusability**: Attributes and methods from the superclass can be reused in the subclass, reducing code duplication.
- **Extended Functionality**: The subclass can add new features or modify existing ones inherited from the superclass.
- **Code Organization**: Inheritance helps to organize code hierarchically, making it easier to manage and maintain.

#### Implementing Inheritance in Java
- In Java, inheritance is implemented using the **extends** keyword. A subclass inherits from a superclass with the command **class Subclass extends Superclass**.

```Java
// Superclass
class Animal {
    String name;

    // Superclass constructor
    public Animal(String name) {
        this.name = name;
    }

    // Superclass method
    public void makeSound() {
        System.out.println("Animal sound");
    }
}

// Subclass extending the superclass
class Dog extends Animal {
    String breed;

    // Subclass constructor
    public Dog(String name, String breed) {
        super(name);  // Call superclass constructor
        this.breed = breed;
    }

    // Subclass method
    @Override
    public void makeSound() {
        super.makeSound();  // Call superclass method
        System.out.println("Bark");
    }
}
```
- In this example, the **Dog** class extends the **Animal** class. **Dog** can use the attributes and methods of **Animal** and also add its own features.
