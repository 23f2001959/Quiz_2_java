
# ✅ **WEEK 8 — FULL DETAILED EXPLANATION (Proper & Easy)**

Topics covered:

1. **Cloning in Java**
2. **Shallow vs Deep Copy**
3. **clone() method, inheritance issues**
4. **Type inference (var keyword)**
5. **Higher-order functions in Java**
6. **Functional Interfaces**
7. **Lambda Expressions**
8. **Method References**
9. **Streams API (Java 8)**

---

# ⭐ 1. **Cloning in Java**

### **What is cloning?**

Cloning means **creating an exact copy of an existing object**.

In Java, cloning is done using:

```java
protected Object clone() throws CloneNotSupportedException
```

👉 clone() is defined in the `Object` class
👉 It returns a **shallow copy** by default
👉 To enable clone(), a class must implement **Cloneable**

---

# ⭐ 2. **Reference Assignment vs Copying**

### **A. Primitive Types (int, double, boolean)**

```java
int x = 5;
int y = x;
y = 10;
```

✔ x stays 5
✔ New copy is created
✔ No aliasing (no shared memory)

---

### **B. Objects**

```java
Employee e1 = new Employee("Alice");
Employee e2 = e1;   // Not a copy
```

✔ Only **one** Employee object is created
✔ e1 and e2 point to the same memory
✔ Changing e2.name also changes e1.name
👉 This is *reference assignment*, **NOT cloning**

---

# ⭐ 3. **Shallow Copy vs Deep Copy**

## **Shallow Copy**

Only the **top-level object** is copied.
Nested objects are **shared**.

Example:

```java
Employee e2 = (Employee) e1.clone();
```

If Employee contains:

```java
Date birthday;
```

Then:

✔ e1.birthday and e2.birthday refer to the **same** Date object
❌ Changing one affects the other

---

## **Deep Copy**

Everything is copied **recursively**, including nested objects.

```java
@Override
public Employee clone() throws CloneNotSupportedException {
    Employee cloned = (Employee) super.clone();
    cloned.birthday = (Date) birthday.clone();
    return cloned;
}
```

Now:

✔ e1.birthday ≠ e2.birthday
✔ No shared memory
👍 Safe copy

---

# ⭐ 4. **clone() and Inheritance Issues**

If a class has subclasses:

```java
class Manager extends Employee {
    Date promotionDate;
}
```

You must deep-copy child class fields also:

```java
@Override
public Manager clone() throws CloneNotSupportedException {
    Manager cloned = (Manager) super.clone();
    cloned.promotionDate = (Date) promotionDate.clone();
    return cloned;
}
```

If subclass doesn't override `clone()`:
👉 Deep copy only happens for parent fields
👉 Child nested fields remain shallow → **bug**

---

# ⭐ 5. **Why clone() Throws Exception?**

`CloneNotSupportedException` occurs if the class does NOT implement `Cloneable`.

---

# ⭐ 6. **Java is Strongly Typed**

You must specify type:

```java
String s = "hello";
```

But Java 10 introduced: **var**

---

# ⭐ 7. **Type Inference with var**

### **Good:**

```java
var name = "John";    // String
var age = 25;         // int
var emp = new Employee();  // Employee
```

✔ Java infers the type from right-hand expression
✔ Works only inside methods (local variables)

### **Bad:**

```java
var x;   // ❌ ERROR — no initial value
```

---

# ⭐ 8. **Higher Order Functions in Java**

A **higher-order function** is a function that:

✔ Accepts another function
or
✔ Returns another function

Java originally could NOT pass functions directly.
Instead, Java used **interfaces** — mainly **functional interfaces**.

Example: **Comparable, Comparator, Runnable**

---

# ⭐ 9. **Callback Example**

Timer calls a method on another object when finished.

Java style:

```java
class MyClass implements TimerOwner {
    public void timerDone() { ... }
}
```

Timer accepts object of TimerOwner → calls `timerDone()`.

So Java passes functions via **objects containing methods**.

---

# ⭐ 10. **Sorting with Comparator before lambdas**

```java
Arrays.sort(arr, new Comparator<String>() {
    public int compare(String a, String b) {
        return a.length() - b.length();
    }
});
```

Long and annoying.

---

# ⭐ 11. **Functional Interfaces**

Interface with **exactly ONE abstract method**.

Examples:

• Runnable → run()
• Comparator → compare()
• Callable → call()

Used for **lambda expressions**

---

# ⭐ 12. **Lambda Expressions**

Shorter way to pass functions.

### Before (old Java)

```java
Comparator<String> c = new Comparator<>() {
    public int compare(String s1, String s2) {
        return s1.length() - s2.length();
    }
};
```

### After (lambda)

```java
Comparator<String> c = (s1, s2) -> s1.length() - s2.length();
```

Or directly:

```java
Arrays.sort(arr, (a, b) -> a.length() - b.length());
```

✔ Short
✔ No class
✔ No boilerplate

---

# ⭐ 13. **Method References**

Use existing methods directly.

Example:

```java
Arrays.sort(words, MyClass::compareByLength);
```

If method exists:

```java
public static int compareByLength(String s1, String s2) {
    return s1.length() - s2.length();
}
```

---

# ⭐ 14. **Streams in Java**

Streams = Modern way to process collections in a **declarative** style.

Example:

```java
list.stream().filter(x -> x > 10).map(x -> x * 2).forEach(System.out::println);
```

## 3 Phases:

1. Create
2. Intermediate operations (filter, map, flatMap, limit)
3. Terminal operations (count, findFirst, collect)

---

# ⭐ 15. **Creating Streams**

### From List

```java
list.stream();
```

### From Array

```java
Stream.of(array);
```

### Using generate()

```java
Stream.generate(() -> "Hello");
```

### Using iterate()

```java
Stream.iterate(0, n -> n + 1);
```

### Bounded iterate

```java
Stream.iterate(0, n -> n < 20, n -> n + 2);
```

---

# ⭐ 16. **Intermediate Operations**

✔ filter()
✔ map()
✔ flatMap()
✔ limit(), skip()
✔ takeWhile(), dropWhile()

Example map:

```java
words.stream()
     .map(w -> w.substring(0, 1))
     .forEach(System.out::println);
```

---

# ⭐ 17. **Terminal Operations**

✔ count()
✔ max(), min()
✔ findFirst(), findAny()

Example:

```java
long count = list.stream().count();
```

---

# ⭐ 18. **Optional**

Used when result can be empty.

Example:

```java
Optional<String> s = words.stream()
                          .filter(w -> w.length() > 20)
                          .findFirst();
```

If no word > 20 chars → returns Optional.empty()

---

# ⭐ 19. **Stream Pipeline Analogy**

Source → filter/map → result
Think of water flowing through pipes.

---
