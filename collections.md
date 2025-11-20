Here is the **MOST COMPLETE + CLEAN + EASY** explanation of **Collections in Java**, covering **every subset**, **their key features**, and **one example for each**.
Perfect for **viva, exam, interview**. ✔️🔥

---

# 🌟 **WHAT IS COLLECTION IN JAVA?**

The **Java Collection Framework (JCF)** is a set of **classes & interfaces** used to store and manipulate groups of objects.
It allows:

* Dynamic size
* Built-in methods (add, remove, search, sort)
* Ready-to-use data structures

---

# 🌳 **COLLECTION HIERARCHY**

```
                Iterable
                    |
                Collection
     ----------------|-----------------
     |               |                |
    List             Set             Queue
                      
                  + Map (Key-Value)
```

---

# 🚀 NOW: **EVERY SUBSET + KEY FEATURES + ONE EXAMPLE**

---

# 🔵 **1. LIST INTERFACE**

✔ Ordered
✔ Allows duplicates
✔ Index-based access
✔ Can store multiple same items

### **Implementations**

1. ArrayList
2. LinkedList
3. Vector
4. Stack

---

## ⭐ **1.1 ARRAYLIST**

### **Key Features:**

* Dynamic array
* Fast access (index-based)
* Slow at inserting in middle

### **Example**

```java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add("A");
System.out.println(list);   // [A, B, A]
```

---

## ⭐ **1.2 LINKEDLIST**

### **Key Features:**

* Doubly linked list
* Fast insertion/deletion

### **Example**

```java
LinkedList<Integer> nums = new LinkedList<>();
nums.add(10);
nums.addFirst(5);
System.out.println(nums);  // [5, 10]
```

---

## ⭐ **1.3 VECTOR**

### **Key Features:**

* Synchronized (thread-safe)
* Slower than ArrayList

### **Example**

```java
Vector<String> v = new Vector<>();
v.add("X");
v.add("Y");
System.out.println(v);     // [X, Y]
```

---

## ⭐ **1.4 STACK**

### **Key Features:**

* LIFO (Last In First Out)
* push(), pop()

### **Example**

```java
Stack<Integer> stack = new Stack<>();
stack.push(1);
stack.push(2);
System.out.println(stack.pop());  // 2
```

---

# 🟢 **2. SET INTERFACE**

✔ No duplicates
✔ No index
✔ Mostly faster access
✔ Used when you need unique items

### **Implementations**

1. HashSet
2. LinkedHashSet
3. TreeSet

---

## ⭐ **2.1 HASHSET**

### **Key Features:**

* No order
* Fast (uses hashing)

### **Example**

```java
HashSet<Integer> hs = new HashSet<>();
hs.add(10);
hs.add(20);
hs.add(10);  // ignored
System.out.println(hs);
```

---

## ⭐ **2.2 LINKEDHASHSET**

### **Key Features:**

* Maintains insertion order
* No duplicates

### **Example**

```java
LinkedHashSet<String> lhs = new LinkedHashSet<>();
lhs.add("Dog");
lhs.add("Cat");
System.out.println(lhs);   // [Dog, Cat]
```

---

## ⭐ **2.3 TREESET**

### **Key Features:**

* Sorted (ascending)
* No duplicates

### **Example**

```java
TreeSet<Integer> ts = new TreeSet<>();
ts.add(3);
ts.add(1);
ts.add(2);
System.out.println(ts);  // [1, 2, 3]
```

---

# 🟡 **3. QUEUE INTERFACE**

✔ FIFO (First In First Out)
✔ Used in scheduling, waiting lines
✔ Some queues give priority

### **Implementations**

1. LinkedList (as Queue)
2. PriorityQueue
3. ArrayDeque

---

## ⭐ **3.1 QUEUE USING LINKEDLIST**

### **Key Features:**

* FIFO
* fast insertion and deletion

### **Example**

```java
Queue<String> q = new LinkedList<>();
q.add("A");
q.add("B");
System.out.println(q.poll());  // A
```

---

## ⭐ **3.2 PRIORITYQUEUE**

### **Key Features:**

* Removes element with highest priority (smallest value by default)
* Not FIFO

### **Example**

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.add(30);
pq.add(10);
pq.add(20);
System.out.println(pq.poll());  // 10
```

---

## ⭐ **3.3 ARRAYDEQUE**

### **Key Features:**

* Faster than Stack
* Supports both ends (double ended queue)

### **Example**

```java
ArrayDeque<Integer> ad = new ArrayDeque<>();
ad.addFirst(1);
ad.addLast(2);
System.out.println(ad);  // [1, 2]
```

---

# 🔴 **4. MAP INTERFACE (NOT part of Collection)**

✔ Key → Value pairs
✔ Key must be unique
✔ Value can duplicate
✔ Used when data is associated (RollNo–Name)

### **Implementations**

1. HashMap
2. LinkedHashMap
3. TreeMap
4. Hashtable

---

## ⭐ **4.1 HASHMAP**

### **Key Features:**

* Fast
* No order maintained
* 1 null key allowed

### **Example**

```java
HashMap<Integer, String> hm = new HashMap<>();
hm.put(1, "A");
hm.put(2, "B");
hm.put(1, "C"); // updates
System.out.println(hm); // {1=C, 2=B}
```

---

## ⭐ **4.2 LINKEDHASHMAP**

### **Key Features:**

* Maintains insertion order
* Fast lookup

### **Example**

```java
LinkedHashMap<Integer, String> lhm = new LinkedHashMap<>();
lhm.put(10, "Dog");
lhm.put(20, "Cat");
System.out.println(lhm);   // {10=Dog, 20=Cat}
```

---

## ⭐ **4.3 TREEMAP**

### **Key Features:**

* Sorted by key
* No null key

### **Example**

```java
TreeMap<Integer, String> tm = new TreeMap<>();
tm.put(30, "Z");
tm.put(10, "X");
tm.put(20, "Y");
System.out.println(tm);  // {10=X, 20=Y, 30=Z}
```

---

## ⭐ **4.4 HASHTABLE**

### **Key Features:**

* Thread-safe (synchronized)
* No null key/value

### **Example**

```java
Hashtable<String, Integer> ht = new Hashtable<>();
ht.put("One", 1);
ht.put("Two", 2);
System.out.println(ht);
```

---

# 🧠 **EXTRA IMPORTANT PARTS**

---

# 🔹 **Iterator Example**

```java
Iterator<String> it = list.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}
```

---

# 🔹 **Collections Utility Class**

```java
Collections.sort(list);
Collections.reverse(list);
Collections.shuffle(list);
```

---

# 🏁 **FINAL SUMMARY TABLE**

| Subset | Class         | Key Feature          |
| ------ | ------------- | -------------------- |
| List   | ArrayList     | Fast access, dynamic |
| List   | LinkedList    | Fast insert/delete   |
| List   | Vector        | Thread-safe          |
| List   | Stack         | LIFO                 |
| Set    | HashSet       | No order, fast       |
| Set    | LinkedHashSet | Insertion order      |
| Set    | TreeSet       | Sorted               |
| Queue  | LinkedList    | FIFO                 |
| Queue  | PriorityQueue | Priority based       |
| Queue  | ArrayDeque    | Double-ended         |
| Map    | HashMap       | Fast, no order       |
| Map    | LinkedHashMap | Ordered              |
| Map    | TreeMap       | Sorted keys          |
| Map    | Hashtable     | Thread-safe          |

---
