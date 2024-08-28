---
title : "Dependency Injection"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2.2 </b> "
---

**Dependency Injection (DI)** is a method that helps reduce dependencies between components (or classes) in an application.
In DI, an instance's dependencies are not created within that instance, but are provided from the outside.

#### Example
``` java
public class Girl {
    private Bikini outfit; // Each girl will have a bikini
    public Girl() {
        outfit = new Bikini(); // When you create a girl, she will wear a bikini
    }
}
```

Through this code above, you will see that when you create a **Girl**, you will create a **Bikini** set with that girl. At this time, **Bikini** is a dependency of **Girl**.

Suppose you want the girl to wear a dress, not the bikini, or the bikini is torn (**Bikini** code does not work), it will directly affect **Girl**

According to that, the rule is Classes should not depend on low-level inheritance, but should depend on Abstraction (abstract class).

``` java
// A interface for outfit
public interface Outfit {
    public void wear();
}

// low-level object, implement Outfit
public class Bikini implements Outfit {
    public void wear() {
        System.out.println("Đã mặc Bikini");
    }
}

// Now Girl only depend on Outfit. If you want to change the girl's outfit, you just need to give the Outfit a new instance.
public class Girl{
    private Outfit outfit;
    public Girl(){
        outfit = new Bikini();
    }
}
```

Up to this point, you have only abstracted **Girl**'s attributes, but actually, **Girl** is still tied to a single **Bikini** set. So if you want to change a girl's clothes, what should you do?

``` java
public class Girl{
    private Outfit outfit;
    public Girl(Outfit anything){
        this.outfit = anything // Initialize a Girl, with any outfit
        // Does not depend too much on initialization time or code.
    }
}

public class Main {
    public static void main(String[] args) {
        Outfit bikini = new Bikini(); // Initialize Bikini instance outside Girl instance
        Girl girl = new Girl(bikini); // girl wear the outfit when initialize her
    }
}

```

With the code above, we have almost completely separated **Bikini** from **Girl**. This reduces the dependency between Girl and Bikini, which increases customization and flexibility for the code.

Now **Girl** will only work with **Outfit**. If you want the girl to wear something else, you just need to create a Class that inherits Outfit and Inject it into **Girl**.

#### Option to inject dependency into an instance
- Constructor injection
- Setter injection
- Interface injection

#### Conclusion
Dependency Injection means that **Objects** should depend on **Abstract Classes** and their details will be injected into the instance at runtime.


