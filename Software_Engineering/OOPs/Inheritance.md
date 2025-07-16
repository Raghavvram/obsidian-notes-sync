### **1. Single Inheritance**
**Definition:** A subclass inherits directly from one superclass.

**Example:**
```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```
**Usage:**
```java
public class Test {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.sound();  // inherited
        d.bark();   // own method
    }
}
```

---

### **2. Multilevel Inheritance**
**Definition:** A class inherits from a subclass which in turn inherits from another class—creating a chain.

**Example:**
```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

class Puppy extends Dog {
    void weep() {
        System.out.println("Puppy weeps");
    }
}
```
**Usage:**
```java
public class Test {
    public static void main(String[] args) {
        Puppy p = new Puppy();
        p.eat();
        p.bark();
        p.weep();
    }
}
```

---

### **3. Hierarchical Inheritance**
**Definition:** Multiple subclasses inherit from a single superclass.

**Example:**
```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("Cat meows");
    }
}
```
**Usage:**
```java
public class Test {
    public static void main(String[] args) {
        Dog d = new Dog();
        Cat c = new Cat();
        d.eat();
        d.bark();
        c.eat();
        c.meow();
    }
}
```

---

### **4. Hybrid Inheritance (Using Interfaces)**
**Definition:** A combination of two or more types of inheritance. Java doesn't support hybrid or multiple inheritance with classes directly, but it can be achieved using interfaces.

**Example:**
```java
interface Printable {
    void print();
}

interface Showable {
    void show();
}

class A {
    void sayHello() {
        System.out.println("Hello from class A");
    }
}

class B extends A implements Printable, Showable {
    public void print() {
        System.out.println("Print method");
    }

    public void show() {
        System.out.println("Show method");
    }
}
```
**Usage:**
```java
public class Test {
    public static void main(String[] args) {
        B obj = new B();
        obj.sayHello();
        obj.print();
        obj.show();
    }
}
```

---

### ⚠️ **Note on Multiple Inheritance**
Java **doesn't support multiple inheritance using classes** to avoid ambiguity (e.g., the *Diamond Problem*). However, multiple inheritance **is supported using interfaces**.

---

In Java, **multiple inheritance using interfaces** is a powerful way to allow a class to inherit behavior from more than one source. Since Java doesn’t support multiple inheritance with *classes* (to avoid ambiguity issues like the Diamond Problem), interfaces provide a clean and safe alternative.

---

### ✅ **Multiple Inheritance with Interfaces — Example**

Here’s a detailed Java example that demonstrates how a class can inherit from multiple interfaces:

```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

// A class implementing multiple interfaces
class Duck implements Flyable, Swimmable {
    public void fly() {
        System.out.println("Duck is flying!");
    }

    public void swim() {
        System.out.println("Duck is swimming!");
    }
}
```

**Usage:**
```java
public class Test {
    public static void main(String[] args) {
        Duck d = new Duck();
        d.fly();   // Output: Duck is flying!
        d.swim();  // Output: Duck is swimming!
    }
}
```

---

### 🧠 **Why It Works**
- Interfaces only declare *what* should be done (method signatures), not *how*.
- There’s no conflict unless two interfaces provide the same default method (which can be resolved using `super.interfaceName.method()`).

Would you like to see an example where two interfaces have default methods with the same name—and how to resolve it? It’s a neat little trick in Java!