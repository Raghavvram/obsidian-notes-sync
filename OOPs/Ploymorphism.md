Dynamic Method Dispatch (also called **Runtime Polymorphism**) is one of the core concepts of Java's object-oriented design. It refers to the process where a call to an **overridden method** is resolved **at runtime** rather than compile time.

---

### 🌟 **Definition**
Dynamic Method Dispatch allows Java to decide **which version** of a method to execute **based on the object's actual type**, not the reference type.

---

### 🔧 **How It Works**
If a superclass reference points to a subclass object, and both classes have overridden a method, then the **subclass version is called** at runtime.

---

### 📘 **Example:**
```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();  // Superclass reference to subclass object
        a.makeSound();         // Output: Dog barks (resolved at runtime)
    }
}
```

Even though `a` is of type `Animal`, the actual object it points to is a `Dog`, so the overridden method in `Dog` is executed.

---

### 🤔 **Why It Matters**
- Enables **flexibility** and **extensibility** in code
- Supports **method overriding**, a key component of polymorphism
- Commonly used in frameworks and APIs that rely on runtime behavior (e.g., Java collections, Spring framework)

Want to see how this works with abstract classes or interfaces too? It gets even more interesting!