## ☕ Java Interview Q&A Cheat Sheet

### 🔁 Method Overriding & Overloading

| **Question** | **Answer** | **Explanation** |
|-------------|------------|-----------------|
| Can we override a static method in Java? | ❌ No | Static methods are bound at compile-time and belong to the class, not the instance. |
| Can we override a private method in Java? | ❌ No | Private methods are not visible to subclasses, so they can't be overridden. |
| Can we override a protected method in Java? | ✅ Yes | Protected methods are accessible in subclasses and can be overridden. |
| Can we override a catch block in Java? | ❌ No | Catch blocks are not methods; they handle exceptions and cannot be overridden. |
| Can we override the `start()` method in Java? | ✅ Yes | You can override `start()` in a thread class, but it's better to override `run()`. |
| Can we override only a few methods of an interface in Java? | ✅ Yes | But the class must be declared `abstract` if it doesn't implement all methods. |

---

### 🧱 Constructors & Object Instantiation

| **Question** | **Answer** | **Explanation** |
|-------------|------------|-----------------|
| Can a constructor be `final`, `static`, or `synchronized`? | ❌ No | Constructors can't be `final` or `static` because they aren't inherited or class-level. |
| Can a constructor be inherited? | ❌ No | Constructors are not inherited; subclasses must define their own. |
| Can abstract classes have constructors? | ✅ Yes | Abstract classes can have constructors to initialize common fields. |
| Can abstract classes be instantiated? | ❌ No | Abstract classes cannot be instantiated directly. |
| What happens if you don't call `super()` in a subclass constructor? | Compiler inserts it | Java automatically inserts a call to the no-arg constructor of the superclass. |

---

### 🧠 Object Behavior & Equality

| **Question** | **Answer** | **Explanation** |
|-------------|------------|-----------------|
| Difference between `a.equals(b)` and `a = b`? | `.equals()` compares values, `=` assigns | `equals()` checks content equality; `=` assigns references. |
| Can a `null` be cast to any type in Java? | ✅ Yes | `null` can be cast to any reference type, but using it causes `NullPointerException`. |
| Is it possible to make an object immutable without `final` keyword? | ✅ Yes | Use private fields, no setters, and return copies of mutable objects. |
| What is object slicing? | Loss of subclass data | Happens when a subclass object is assigned to a superclass reference, losing subclass-specific fields. |

---

### 🧪 Exception Handling

| **Question** | **Answer** | **Explanation** |
|-------------|------------|-----------------|
| What happens if a `finally` block has a return statement? | It overrides other returns | The return in `finally` will suppress returns from `try` or `catch`. |
| Is it possible for `finally` to not execute? | ✅ Rarely | If JVM exits (`System.exit()`), or thread is killed, `finally` may not run. |
| Can you catch `Throwable`? Should you? | ✅ Yes, ❌ Not recommended | Catching `Throwable` includes `Error`s, which are usually unrecoverable. |

---

### 🧰 Interfaces & Abstract Classes

| **Question** | **Answer** | **Explanation** |
|-------------|------------|-----------------|
| Can we implement one interface from another interface? | ✅ Yes | Interfaces can extend other interfaces. |
| Can we create an object of an interface? | ❌ No | Interfaces can't be instantiated directly. |
| Can we overload methods of an interface? | ✅ Yes | Overloading is allowed as long as parameter lists differ. |
| Can we declare a method in an interface as `final`? | ❌ No | Interface methods are implicitly `abstract` and cannot be `final`. |

---

### 🧩 Miscellaneous

| **Question** | **Answer** | **Explanation** |
|-------------|------------|-----------------|
| Can we call the `main()` method from another class? | ✅ Yes | It's just a static method and can be called like any other. |
| Is it possible to compile and run a Java program without `main()`? | ✅ Pre-Java 7 only | Static blocks could run code, but from Java 7+, `main()` is required. |
| Can two methods in a class have the same name and parameters? | ❌ No | Method signature must differ (name or parameter types/count). |
| Can a subclass object be assigned to a superclass reference? | ✅ Yes | This is called upcasting and is allowed in Java. |
| Can abstract classes have a `main()` method? | ✅ Yes | Abstract classes can have static methods including `main()`. |
| Can a class be `protected`? | ❌ No | Top-level classes can only be `public` or package-private. |
| What is the default value of a local variable? | ❌ None | Local variables must be explicitly initialized before use. |
| What is the default access modifier (package-private)? | No keyword | Accessible only within the same package. |

---

