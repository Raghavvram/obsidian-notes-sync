The **Decorator Design Pattern** is like adding toppings to your dosa: the dosa is the same, but you layer on chutney, podi, maybe even cheese, depending on what flavor you’re after — without changing how the dosa is made at its core.

---

### 🌯 Layman's Analogy: Customizing Your Dosa

- You start with a **plain dosa**.
- Then you **add podi** on top.
- Then **add cheese**.
- Maybe even a **vegetable filling**.

Now it tastes different — **richer and more powerful** — but you didn’t need a new dosa recipe for every combination. You just *wrapped* the basic dosa with enhancements.

That’s what the **Decorator Pattern** does: it adds new responsibilities or features to an existing object, **dynamically**, without altering its structure.

---

### 🧠 When to Use It?

- You want to **add or remove behavior** at runtime.
- You want to avoid an explosion of subclasses (e.g., `TextView`, `ScrollableTextView`, `BorderedScrollableTextView`, etc.).
- You want to **extend an object’s behavior** without modifying its code (open/closed principle).

---

### 💻 Java Example: Adding Features to a Coffee

Let’s decorate a simple `Coffee` object with **milk** and **sugar**!

#### Step 1: The Component Interface

```java
interface Coffee {
    String getDescription();
    double cost();
}
```

---

#### Step 2: Concrete Component

```java
class SimpleCoffee implements Coffee {
    public String getDescription() {
        return "Simple Coffee";
    }

    public double cost() {
        return 5.0;
    }
}
```

---

#### Step 3: Abstract Decorator

```java
abstract class CoffeeDecorator implements Coffee {
    protected Coffee coffee;

    public CoffeeDecorator(Coffee coffee) {
        this.coffee = coffee;
    }
}
```

---

#### Step 4: Concrete Decorators

```java
class MilkDecorator extends CoffeeDecorator {
    public MilkDecorator(Coffee coffee) {
        super(coffee);
    }

    public String getDescription() {
        return coffee.getDescription() + ", Milk";
    }

    public double cost() {
        return coffee.cost() + 1.5;
    }
}

class SugarDecorator extends CoffeeDecorator {
    public SugarDecorator(Coffee coffee) {
        super(coffee);
    }

    public String getDescription() {
        return coffee.getDescription() + ", Sugar";
    }

    public double cost() {
        return coffee.cost() + 0.5;
    }
}
```

---

#### Step 5: Usage

```java
public class Main {
    public static void main(String[] args) {
        Coffee plainCoffee = new SimpleCoffee();

        Coffee milkCoffee = new MilkDecorator(plainCoffee);
        Coffee fancyCoffee = new SugarDecorator(milkCoffee);

        System.out.println(fancyCoffee.getDescription()); // Simple Coffee, Milk, Sugar
        System.out.println("Cost: ₹" + fancyCoffee.cost()); // Cost: ₹7.0
    }
}
```

---

### 🧵 Summary

- **Core object stays the same**, but you wrap it with new functionality.
- You can chain decorators flexibly and **compose behavior** without subclassing.
- Great for UI frameworks, file streams, or any extensible feature set.
