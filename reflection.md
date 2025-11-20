Here is a **very simple, clear explanation of Reflection in Java WITH easy basic examples** — perfect for viva/exam 👇

---

# ✅ **What is Reflection in Java?**

**Reflection** is a feature in Java that lets your program:

* **Inspect** a class (find its methods, fields, constructors)
* **Modify** it (change field values, call methods)
* **At runtime** (while program is running)

In simple words:

> **Reflection = seeing and changing the structure of a class during runtime.**

---

# ⭐ **Why do we use Reflection?**

Because sometimes you **don’t know which class you need until runtime**.

Used in:

* Spring / Hibernate (Dependency Injection)
* JUnit (to call test methods)
* IDEs (like IntelliJ, Eclipse)
* Debuggers / Frameworks
* Serialization

---

# 🧪 BASIC EXAMPLE — Step-by-step

## **Example 1: Get Class Information**

```java
class Student {
    private String name;
    public void show() {
        System.out.println("Hello");
    }
}

public class Test {
    public static void main(String[] args) throws Exception {
        Class<?> c = Class.forName("Student");
        System.out.println("Class name: " + c.getName());
    }
}
```

**Output:**

```
Class name: Student
```

---

# **Example 2: List All Methods of a Class**

```java
Class<?> c = Class.forName("Student");

Method[] methods = c.getMethods();

for (Method m : methods) {
    System.out.println(m.getName());
}
```

This prints all methods of `Student` (including inherited ones).

---

# **Example 3: Create Object Using Reflection**

```java
Class<?> c = Class.forName("Student");

Object obj = c.newInstance();  // creates Student object

System.out.println("Object created: " + obj);
```

---

# **Example 4: Call a Method Using Reflection**

```java
Class<?> c = Class.forName("Student");

Object obj = c.newInstance();

Method m = c.getMethod("show");   // get method
m.invoke(obj);                    // call method
```

**Output:**

```
Hello
```

---

# **Example 5: Access Private Field**

```java
Class<?> c = Class.forName("Student");

Object obj = c.newInstance();

Field f = c.getDeclaredField("name");
f.setAccessible(true);             // allow private access
f.set(obj, "Manish");              // set value

System.out.println(f.get(obj));    // print value
```

---

# ⚠️ **Disadvantages of Reflection**

* **Slow** (runtime operations)
* **Breaks encapsulation** (can access private fields)
* **Not type-safe** (errors at runtime)
* **Hard to maintain**

---
