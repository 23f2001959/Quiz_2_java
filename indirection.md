Here is a **simple, clean, viva-friendly explanation of *Indirection in Java*** 👇

---

# ✅ **What is Indirection in Java?**

**Indirection** means **accessing something *through* another layer**, instead of accessing it directly.

In simple words:

> **Indirection = Not doing something directly → but doing it through another object, method, interface, or pointer-like reference.**

It is a **design principle** used to make code:

* more flexible
* more maintainable
* more loosely coupled

---

# ⭐ **Why is Indirection used?**

Because it helps:

* hide details
* reduce dependency
* increase abstraction
* allow easier modification

---

# 🔍 **Simple Real-Life Example**

If you want water:

* **Direct Access:** Go directly to the tank on the roof
* **Indirect Access:** Turn on the tap (tap → pipe → tank)

The tap is *indirection*.

---

# 🔥 **Indirection in Java (with simple examples)**

---

# **1️⃣ Using Method Calls (Basic Indirection)**

Instead of accessing fields directly:

```java
class Student {
    private String name;

    public String getName() {     // indirection
        return name;
    }
}
```

Here:

* You don’t access the field directly.
* You go **through the getter method** → this is indirection.

---

# **2️⃣ Using Interfaces (Most Important Indirection)**

```java
interface Animal {
    void sound();
}

class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();    // indirection
        a.sound();
    }
}
```

Here:

* You call the method through the **Animal interface**, not directly on Dog.
* This allows flexibility → you can replace Dog with Cat later.

This is a core principle of **polymorphism**.

---

# **3️⃣ Using References Instead of Objects (Another Indirection)**

```java
List<String> list = new ArrayList<>();
```

You use the **List** interface reference (indirection) to access `ArrayList`.

---

# **4️⃣ Using Dependency Injection (Framework Indirection)**

In Spring:

```java
@Autowired
PaymentService service;
```

You never create the object directly.
Spring gives you the object → **indirection**.

---

# **5️⃣ Using Wrappers (Indirect Access to Primitive)**

```java
Integer x = new Integer(10);
```

You are not using the primitive directly → wrapper adds indirection.

---

# 📦 **One-Line Viva Definition**

> **Indirection in Java means accessing an object, value, or functionality through another layer instead of directly, which increases abstraction and flexibility.**

---

# ⭐ Shraddha-friendly super short explanation ❤️

**Indirection = Doing things indirectly (through another layer).
Examples: getters, interfaces, references, DI, wrappers.**

---
