### 🟠 1. **Single Responsibility Principle (SRP)**
*A class should have only one reason to change.*

Your `ManageBird` class currently handles **bird behavior decisions** *and* **printing behavior**—two responsibilities. Let’s break that down.

#### ✅ Modified Code for SRP:
```java
class BirdBehavior {
    void performBehavior(String name) {
        if (name.equals("parrot")) {
            new Parrot().perform();
        } else if (name.equals("sparrow")) {
            new Sparrow().perform();
        } else {
            new UnknownBird().perform();
        }
    }
}

class Parrot {
    void perform() {
        System.out.println("Speak");
        System.out.println("fly");
    }
}

class Sparrow {
    void perform() {
        System.out.println("fly");
        System.out.println("chips");
    }
}

class UnknownBird {
    void perform() {
        System.out.println("fly");
        System.out.println("drink");
    }
}
```

#### 📌 Explanation:
- The responsibility of *selecting* a bird is in `BirdBehavior`.
- Each bird class now handles its *own* behavior.

---

### 🟠 2. **Open/Closed Principle (OCP)**
*Software entities should be open for extension but closed for modification.*

Right now, to add a new bird type, you’d have to change `BirdBehavior`. Let’s make the design extensible using polymorphism.

#### ✅ Modified Code for OCP:
```java
interface Bird {
    void perform();
}

class Parrot implements Bird {
    public void perform() {
        System.out.println("Speak");
        System.out.println("fly");
    }
}

class Sparrow implements Bird {
    public void perform() {
        System.out.println("fly");
        System.out.println("chips");
    }
}

class UnknownBird implements Bird {
    public void perform() {
        System.out.println("fly");
        System.out.println("drink");
    }
}

class BirdFactory {
    static Bird getBird(String name) {
        return switch(name.toLowerCase()) {
            case "parrot" -> new Parrot();
            case "sparrow" -> new Sparrow();
            default -> new UnknownBird();
        };
    }
}
```

#### 📌 Explanation:
- You can now **add new birds** by adding a new class and updating the factory. `Bird` interface stays unchanged.

---

### 🟠 3. **Liskov Substitution Principle (LSP)**
*Subtypes must be substitutable for their base types.*

Let’s say `Bird` has a `fly()` method, but not all birds (e.g., penguins) can fly. LSP will break if calling `fly()` on a `Penguin` throws an error.

#### ✅ Modified Code for LSP:
```java
interface Bird {
    void perform();
}

interface Flyable {
    void fly();
}

class Parrot implements Bird, Flyable {
    public void perform() {
        System.out.println("Speak");
        fly();
    }

    public void fly() {
        System.out.println("fly");
    }
}

class Penguin implements Bird {
    public void perform() {
        System.out.println("Swim");
    }
}
```

#### 📌 Explanation:
- `Flyable` is separated from `Bird`. So `Penguin` is **not forced** to implement flying behavior.
- This avoids runtime surprises when substituting a `Penguin` in code expecting a `Bird`.

---

### 🟠 4. **Interface Segregation Principle (ISP)**
*No client should be forced to depend on methods it does not use.*

Instead of a monolithic Bird interface with `fly()`, `speak()`, `eat()`, let’s create **segregated interfaces**.

#### ✅ Modified Code for ISP:
```java
interface Bird {
    void perform();
}

interface Flyable {
    void fly();
}

interface Speakable {
    void speak();
}

class Parrot implements Bird, Flyable, Speakable {
    public void perform() {
        speak();
        fly();
    }

    public void speak() {
        System.out.println("Speak");
    }

    public void fly() {
        System.out.println("fly");
    }
}
```

#### 📌 Explanation:
- Clients like `Penguin` aren’t forced to implement `Flyable` or `Speakable` if they don’t need it.
- Keeps interfaces **clean and focused**.

---

### 🟠 5. **Dependency Inversion Principle (DIP)**
*High-level modules should not depend on low-level modules. Both should depend on abstractions.*

Let’s restructure the code so `BirdBehavior` depends on abstractions (`Bird`), not concrete classes.

#### ✅ Modified Code for DIP:
```java
interface Bird {
    void perform();
}

class BirdBehavior {
    private final Bird bird;

    BirdBehavior(Bird bird) {
        this.bird = bird;
    }

    void execute() {
        bird.perform();
    }
}
```

#### 📌 Usage Example:
```java
Bird parrot = new Parrot();
BirdBehavior behavior = new BirdBehavior(parrot);
behavior.execute();
```

#### 📌 Explanation:
- `BirdBehavior` doesn’t care *what* kind of bird it’s interacting with—it only relies on the `Bird` abstraction.
- This reduces coupling and boosts flexibility.
---
</br></br>

---
Let’s reimagine the **SOLID principles** through the lens of superheroes. 🦸‍♂️🦸‍♀️

---

### **S – Single Responsibility Principle (SRP)**  
**🦸 “Every superhero has one core power.”**

You wouldn’t expect Batman to suddenly breathe underwater or Hulk to fly, right? That’s Aquaman’s and Superman’s territory. Each hero has a **single, focused ability** they excel at.

**In code:** A class should do just *one job*—like Batman doing detective work, not performing brain surgery on the side. If a class handles both user login and report generation, it’s trying to be Batman and Iron Man at once. Bad idea.

---

### **O – Open/Closed Principle (OCP)**  
**🧩 “Add new heroes to the team—no need to rewire the Batcave.”**

When a new threat comes along, the Justice League doesn’t rewrite Wonder Woman’s backstory—they call in a new hero with the needed skill. The League is designed to *expand*, not be *rewritten*.

**In code:** Your program should be able to introduce new classes (heroes) to handle new problems (villains), without altering existing, stable code. Think of it like building the Hall of Justice with extra doorways ready for future members.

---

### **L – Liskov Substitution Principle (LSP)**  
**🦹‍♀️ “Don’t replace Superman with someone who forgets how to fly.”**

Imagine replacing Superman with a new hero, only to realize they panic midair and fall. Not cool. A replacement hero should fill the same shoes without ruining the mission.

**In code:** If your base class expects a method to work (like `fly()`), then all subclasses must follow that expectation. If `Penguin` inherits from `Bird` but throws an error when told to fly—it’s breaking the mission.

---

### **I – Interface Segregation Principle (ISP)**  
**🎛️ “Give heroes the gadgets they actually use.”**

Batman’s utility belt isn’t crammed with Aquaman’s trident or Thor’s hammer—it has just the tools he needs. No more, no less.

**In code:** Don’t force a class to implement methods it doesn’t need. If a printer doesn’t fax, don’t make it pretend to. **Customize the interface like a superhero’s toolkit**—made to fit their powers.

---

### **D – Dependency Inversion Principle (DIP)**  
**🧠 “Heroes follow the mission, not the gadget brand.”**

Iron Man doesn’t care if his arc reactor tech comes from Stark or Wakandan science—as long as it powers the suit. Heroes rely on the *concept* of power, not one specific source.

**In code:** High-level components (like a mission controller) should depend on *abstract abilities* (like `PowerSource`), not specific ones (like `StarkBattery`). That way, you can plug in new gadgets or heroes without chaos.

---