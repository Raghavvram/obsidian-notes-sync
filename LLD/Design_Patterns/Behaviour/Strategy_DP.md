**Strategy Design Pattern** — one of those elegant tools that makes your code smarter without making it messier.

---

### 🛵 Layman's Analogy: Choosing a Route in Google Maps

Say you’re traveling from Thullur to Chennai:

- You can go by **car**, **bike**, or **walking**.
- Google Maps doesn’t care how you travel — it just needs to know **which route strategy** to use.
- Each method has its **own logic** for calculating ETA, routes, and traffic.

You choose the *strategy* at runtime, and the rest of the system adapts.

That’s exactly how the **Strategy Pattern** works:
> You define a family of algorithms, encapsulate them, and make them interchangeable at runtime.

---

### 🧠 When to Use It

- When you have **multiple ways to perform a task**, and you want to choose the method dynamically.
- You want to follow the **Open/Closed Principle** — add new behavior without changing existing code.
- A classic case is avoiding too many `if-else` or `switch` statements for decision logic.

---

### 🚦 Java Example: Travel Strategy

Let’s build a `TravelContext` that can switch between different travel strategies: by car, by bike, or by walk.

---

#### Step 1: Strategy Interface

```java
interface TravelStrategy {
    void travel(String destination);
}
```

---

#### Step 2: Concrete Strategies

```java
class CarTravel implements TravelStrategy {
    public void travel(String destination) {
        System.out.println("Driving a car to " + destination);
    }
}

class BikeTravel implements TravelStrategy {
    public void travel(String destination) {
        System.out.println("Riding a bike to " + destination);
    }
}

class WalkTravel implements TravelStrategy {
    public void travel(String destination) {
        System.out.println("Walking to " + destination);
    }
}
```

---

#### Step 3: Context Class

```java
class TravelContext {
    private TravelStrategy strategy;

    public void setStrategy(TravelStrategy strategy) {
        this.strategy = strategy;
    }

    public void goTo(String destination) {
        strategy.travel(destination);
    }
}
```

---

#### Step 4: Demo

```java
public class Main {
    public static void main(String[] args) {
        TravelContext context = new TravelContext();

        context.setStrategy(new CarTravel());
        context.goTo("Chennai");

        context.setStrategy(new WalkTravel());
        context.goTo("Local Market");

        context.setStrategy(new BikeTravel());
        context.goTo("Friend’s House");
    }
}
```

---

### 🧵 Summary

- **Strategy** encapsulates interchangeable logic — like “ways to travel.”
- The **context** delegates the task to the selected strategy.
- You can **swap behaviour on the fly** without changing how the context operates.

This pattern is super useful in games (player behaviour), business rules (payment methods), or analytics (sorting, filtering, scoring).
