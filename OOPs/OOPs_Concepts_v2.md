
### **1. Encapsulation**
**Definition:** Wrapping data (variables) and code (methods) into a single unit and restricting access via access modifiers.

#### **Types based on Access Modifiers:**
- **Private:** Accessible only within the same class.
- **Default (no modifier):** Accessible within the same package.
- **Protected:** Accessible within the package and subclasses.
- **Public:** Accessible from anywhere.

**Example:**
```java
class BankAccount {
    private double balance; // Encapsulated

    public void deposit(double amount) {
        balance += amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

---

### **2. Inheritance**
**Definition:** The mechanism where one class acquires properties and behavior (methods) of another class.

#### **Types:**
- **Single Inheritance:** One class inherits from one superclass.
- **Multilevel Inheritance:** A class inherits from a class which in turn inherits from another class.
- **Hierarchical Inheritance:** Multiple classes inherit from a single superclass.

> 💡 Note: Java **doesn't support** **multiple inheritance** (a class having more than one parent class), but you can achieve similar behavior using interfaces.

**Example:**
```java
class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal { // Single Inheritance
    void bark() {
        System.out.println("Dog barks");
    }
}

class Puppy extends Dog { // Multilevel Inheritance
    void weep() {
        System.out.println("Puppy weeps");
    }
}
```

---

### **3. Abstraction**
**Definition:** Showing only essential features and hiding unnecessary details.

#### **Types:**
- **Abstract Class:** Can have both abstract (without body) and concrete methods.
- **Interface:** Only has method declarations (Java 8+ allows default and static methods).

**Abstract Class Example:**
```java
abstract class Vehicle {
    abstract void start();

    void fuel() {
        System.out.println("Vehicle needs fuel");
    }
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car is starting...");
    }
}
```

**Interface Example:**
```java
interface Flyable {
    void fly();
}

class Bird implements Flyable {
    public void fly() {
        System.out.println("Bird is flying");
    }
}
```

---

### **4. Polymorphism**
**Definition:** Ability of an object to take on many forms.

#### **Types:**
- **Compile-time Polymorphism (Method Overloading):** Multiple methods in the same class with the same name but different parameters.
- **Runtime Polymorphism (Method Overriding):** A subclass provides a specific implementation of a method already defined in its superclass.

**Overloading Example:**
```java
class MathOps {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

**Overriding Example:**
```java
class Parent {
    void show() {
        System.out.println("Parent show()");
    }
}

class Child extends Parent {
    @Override
    void show() {
        System.out.println("Child show()");
    }
}
```

---