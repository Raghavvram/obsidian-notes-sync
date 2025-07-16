### **1. Encapsulation**
**Definition:** Encapsulation is the practice of bundling data (variables) and methods that operate on the data into a single unit (class), and restricting direct access to some of the object's components.

**Example in Java:**
```java
class Person {
    private String name; // private = encapsulated
    private int age;

    // public getters and setters provide controlled access
    public String getName() {
        return name;
    }

    public void setName(String newName) {
        name = newName;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int newAge) {
        age = newAge;
    }
}
```
Here, the fields `name` and `age` are hidden from outside access and can only be accessed/modified via methods.

---

### **2. Inheritance**
**Definition:** Inheritance allows a class (child/subclass) to inherit fields and methods from another class (parent/superclass), enabling code reuse.

**Example in Java:**
```java
class Animal {
    void makeSound() {
        System.out.println("Some sound...");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark!");
    }
}
```
Here, `Dog` inherits from `Animal` and overrides the `makeSound` method.

---

### **3. Abstraction**
**Definition:** Abstraction means hiding the complex implementation details and showing only the essential features of an object.

**Example in Java:**
```java
abstract class Shape {
    abstract void draw(); // abstract method
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing a circle");
    }
}
```
The `Shape` class defines an abstract method `draw()`, and `Circle` provides its specific implementation.

---

### **4. Polymorphism**
**Definition:** Polymorphism means “many forms,” and it allows methods to behave differently based on the object that’s calling them.

**Example in Java:**
```java
class Animal {
    void speak() {
        System.out.println("Animal speaks");
    }
}

class Cat extends Animal {
    void speak() {
        System.out.println("Meow");
    }
}

class Cow extends Animal {
    void speak() {
        System.out.println("Moo");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a1 = new Cat();
        Animal a2 = new Cow();
        a1.speak(); // Meow
        a2.speak(); // Moo
    }
}
```
Even though `a1` and `a2` are of type `Animal`, the overridden `speak()` methods of `Cat` and `Cow` are called at runtime.
