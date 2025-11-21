| Feature                  | HashSet          | LinkedHashSet           | TreeSet                     |
| ------------------------ | ---------------- | ----------------------- | --------------------------- |
| **Duplicates allowed?**  | ❌ No             | ❌ No                    | ❌ No                        |
| **Order maintained?**    | ❌ No             | ✔ Insertion order       | ✔ Sorted order              |
| **Speed**                | ⭐ Fastest        | Medium                  | ❗ Slowest                   |
| **Underlying Structure** | HashTable        | HashTable + Linked List | Red-Black Tree              |
| **Allows null?**         | ✔ Yes (one null) | ✔ Yes (one null)        | ❌ No (NullPointerException) |
