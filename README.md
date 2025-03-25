# Abstraction 
Abstraction is one of the four pillars of Object-Oriented Programming (OOP) (along with Encapsulation,
Inheritance, and Polymorphism). It is all about hiding the details and showing only the relevant features of an object.
Imagine a remote control for your TV. You press the "power" button, and the TV turns on. But do you know exactly 
what happens inside the circuits? Probably not! You just need to know that pressing the button turns it on—that's 
abstraction in action!

In Java, abstraction is used to hide complex logic and expose only the necessary parts to the user.

## How is abstraction implemented in Java?

Java provides two ways to achieve abstraction:
**Abstract Classes (abstract keyword)**
**Interfaces (interface keyword)**

# 1️⃣ Abstract Classes (Partial Abstraction)

1. An abstract class cannot be instantiated **(you can't create objects from it)**.
2. It can have both abstract (no body) and non-abstract methods (with body).
3. Subclasses must implement the abstract methods.

**By the way 💡**
A method without a body is one that only has a declaration (parameters and name, no actual code inside it)

```bash
void startEngine() {  
    System.out.println("Engine is starting...");
}
```

```bash
abstract void startEngine();
```
It just defines that every subclass must have a startEngine() method,
but each subclass must write its own version of what happens when the engine starts.
Since startEngine() is abstract, Java forces every subclass to provide its own version:

```bash
class Car extends Vehicle {
    void startEngine() {  // Now this method has a body!
        System.out.println("Starting the car engine with a key...");
    }
}
```

Let’s say we are making a program for different types of vehicles.

* All vehicles have an engine and can start, but the way they start can be different.
* We want to force all vehicle types to have a startEngine() method without knowing exactly how each one works.
* Some common functionalities (like fuelUp()) can be shared across all vehicles.

```bash
// Abstract class (template for all vehicles)
abstract class Vehicle {  
    // Abstract method (must be implemented in subclasses)
    abstract void startEngine();  

    // Concrete method (shared by all vehicles)
    void fuelUp() {  
        System.out.println("Filling up the fuel tank...");
    }
}

// 🚗 Car class (inherits from Vehicle)
class Car extends Vehicle {  
    // Must define startEngine()
    void startEngine() {
        System.out.println("Starting the car engine with a key...");
    }
}

// 🏍️ Motorcycle class (inherits from Vehicle)
class Motorcycle extends Vehicle {  
    // Must define startEngine()
    void startEngine() {
        System.out.println("Starting the motorcycle engine with a self-start button...");
    }
}

// 🚛 Truck class (inherits from Vehicle)
class Truck extends Vehicle {  
    void startEngine() {
        System.out.println("Starting the truck engine with an air start system...");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle myCar = new Car();  
        Vehicle myBike = new Motorcycle();  
        Vehicle myTruck = new Truck();  

        myCar.startEngine();   // Output: Starting the car engine with a key...
        myBike.startEngine();  // Output: Starting the motorcycle engine with a self-start button...
        myTruck.startEngine(); // Output: Starting the truck engine with an air start system...

        myCar.fuelUp();  // Output: Filling up the fuel tank...
    }
}
```





