### 🔁 What is the Singleton Design Pattern?

**Definition:**  
The Singleton Pattern ensures that a **class has only one instance** and provides a global point of access to it.

---

### 🧠 In Layman Terms:

Imagine you’re building a house. You only need **one water tank** on the roof that supplies water to the whole house. You don’t want each room creating its own tank—that would waste space, water, and money!

Similarly, in programming, there are cases where you want **only one object** of a class to exist—for example, a database connection. The Singleton Pattern lets us create that *one* object and share it everywhere.

---

### ✅ Key Features of Singleton:
- Only **one instance** exists.
- It's **shared** across the application.
- Controlled **access point** through a static method.
- Often used for **logging**, **caching**, **configuration**, or **database connections**.

---

### ☕ Java Example: Singleton for Database Connection

Let’s implement a basic Singleton that represents a database connection.

```java
public class DatabaseConnection {
    // Step 1: Create a private static instance
    private static DatabaseConnection instance;

    // Step 2: Make the constructor private so no one else can instantiate
    private DatabaseConnection() {
        System.out.println("Connected to Database.");
    }

    // Step 3: Provide a public method to get the instance
    public static DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection(); // Create it if it doesn't exist
        }
        return instance;
    }

    public void query(String sql) {
        System.out.println("Executing query: " + sql);
    }
}
```

**Usage:**
```java
public class Main {
    public static void main(String[] args) {
        DatabaseConnection db1 = DatabaseConnection.getInstance();
        db1.query("SELECT * FROM users");

        DatabaseConnection db2 = DatabaseConnection.getInstance();
        db2.query("SELECT * FROM orders");

        // Check if both references point to the same object
        System.out.println(db1 == db2);  // Output: true
    }
}
```

---

### ⚠️ Pro Tip: Thread Safety

If you're working in a **multi-threaded application**, you should make the `getInstance()` method **thread-safe** to avoid creating multiple instances by accident. You can use:
- **Synchronized method/block**
- **Double-checked locking**
- **Early initialization**
