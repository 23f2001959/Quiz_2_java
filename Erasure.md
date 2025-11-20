Here is a **clean, simple, exam-friendly explanation of Type Erasure in Java** 👇

---

# ✅ **What is Type Erasure in Java?**

**Type Erasure** is the process by which **Java removes all generic type information at compile time**.
This means that **generic types exist only during compilation**, and **do not exist at runtime**.

---

# 🔍 **Why does Java use Type Erasure?**

Because Java needs to remain **backward compatible** with older versions (before Java 5, when generics didn’t exist).
Old JVMs should still run new Java code.

---

# ⚙️ **How Type Erasure Works**

Java compiler checks generics at compile time:

### 1️⃣ **Type parameters are removed**

Example:

```java
List<String> names = new ArrayList<>();
```

After type erasure, it becomes:

```java
List names = new ArrayList();
```

### 2️⃣ **Type parameters are replaced with bounds**

If bounded:

```java
class Box<T extends Number> { }
```

After erasure:

```java
class Box {
    Number value;   // T becomes Number
}
```

If unbounded:

```java
class Box<T> { }
```

Erases to:

```java
class Box {
    Object value;
}
```

### 3️⃣ **Bridge methods are created (sometimes)**

To maintain polymorphism when erasing generics.

---

# 🧠 **Key consequences of Type Erasure**

### ❌ 1. **Cannot use generics with primitives**

```java
List<int> nums;  // ❌ error
```

Because generics become Objects → primitives don’t fit.

---

### ❌ 2. **Cannot create generic arrays**

```java
List<String>[] arr = new ArrayList<String>[5]; // ❌
```

---

### ❌ 3. **No runtime generic type information**

```java
List<String> a = new ArrayList<>();
List<Integer> b = new ArrayList<>();

a.getClass() == b.getClass()   // true ✔
```

Because both become `ArrayList`.

---

### ❌ 4. **Cannot check generic type with instanceof**

```java
if (obj instanceof List<String>) { }  // ❌ error
```

Instead:

```java
if (obj instanceof List) { }  // ✔ allowed
```

---

### ❌ 5. **Cannot create new T()**

Because T does not exist at runtime.

```java
class Box<T> {
    T obj = new T(); // ❌ illegal
}
```

---

# 📦 **Simple Example to Understand**

### Code:

```java
List<String> list = new ArrayList<>();
list.add("Hello");
```

**At runtime**, this becomes:

```java
List list = new ArrayList();
list.add("Hello");  // still works
```

Generics disappear completely.

---

