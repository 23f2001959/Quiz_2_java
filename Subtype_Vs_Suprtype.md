Got it — you want **Subtype and Supertype explained specifically in the context of Java Generics**.
Here is the **clearest, exam-friendly explanation** 👇

---

# ✅ **Subtype & Supertype in Java Generics**

In **normal classes**, this rule is true:

```
Dog extends Animal  → Dog is a subtype of Animal
```

But in **generics**, this rule DOES NOT automatically apply.

---

# ❌ **Important Rule**

### **List<Dog> is NOT a subtype of List<Animal>**

Even though:

```
Dog is a subtype of Animal
```

But:

```
List<Dog>  ≠ subtype of  List<Animal>
```

This is called **invariance** in Java generics.

---

# 🔥 Why?

Because if Java allowed it:

```java
List<Dog> dogList = new ArrayList<>();
List<Animal> animals = dogList; // imagine this was allowed
animals.add(new Cat());         // this would add a Cat into List<Dog> ❌
```

That would break type safety.

---

# ✔ So how do we work with subtypes/supertypes in generics?

Java provides **wildcards**:

---

# ✅ **1. ? extends T → Upper-Bounded Wildcard (Subtype)**

Means:
**"Accept any subtype of T"**

Example:

```java
List<? extends Animal> list;
```

This list can contain:

* List<Dog>
* List<Cat>
* List<Cow>

All are allowed because all are **subtypes** of `Animal`.

✔ You can **read** from it
❌ You cannot **add** to it (except null)

---

# 🎯 Simple rule:

### **? extends = you get (read) values of type T**

### **Producer → extends**

(PECS rule: Producer Extends, Consumer Super)

---

# ✅ **2. ? super T → Lower-Bounded Wildcard (Supertype)**

Means:
**"Accept any supertype of T"**

Example:

```java
List<? super Dog> list;
```

This list can be:

* List<Dog>
* List<Animal>
* List<Object>

All are supertypes of `Dog`.

✔ You can **add Dog**
✔ You can add any subtype of Dog
❌ You cannot safely read (returns Object)

---

# 🎯 Simple rule:

### **? super = you can put (write) values of type T**

### **Consumer → super**

(PECS rule: Producer Extends, Consumer Super)

---

# 🔥 Summary Table (Super easy to remember)

| Generic Type             | Meaning                   | Add?  | Read?         |
| ------------------------ | ------------------------- | ----- | ------------- |
| `List<Animal>`           | Only Animal               | ✔ Yes | ✔ Animal      |
| `List<? extends Animal>` | Any **subtype** of Animal | ❌ No  | ✔ Animal      |
| `List<? super Dog>`      | Any **supertype** of Dog  | ✔ Dog | ❌ Only Object |

---

# 📝 **One-Line Viva Answers**

### **Subtype in Generics**

“In generics, `? extends T` accepts any subtype of T.”

### **Supertype in Generics**

“In generics, `? super T` accepts any supertype of T.”

### **Why List<Dog> is not subtype of List<Animal>?**

“To prevent adding wrong types and breaking type safety.”

---

