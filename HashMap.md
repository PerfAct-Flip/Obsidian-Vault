A **HashMap** is a data structure in Java used to store data in **Key-Value pairs**. It is part of the `java.util` package and implements the `Map` interface.

Think of it like a real-world dictionary: the "Word" is the **Key**, and the "Definition" is the **Value**. You use the unique key to look up its associated value instantly.

---

### Key Characteristics

- **Unique Keys:** You cannot have duplicate keys. If you insert a new value with an existing key, the old value is overwritten.
    
- **Duplicate Values:** Multiple different keys can point to the same value.
    
- **Nulls:** It allows one `null` key and multiple `null` values.
    
- **Order:** It does **not** guarantee any specific order of the elements.
    
- **Performance:** It provides $O(1)$ (constant time) performance for basic operations like `get()` and `put()`.
    

---

### Essential HashMap Methods

To use a HashMap, you must specify the types for both the Key and the Value:

HashMap<String, Integer> map = new HashMap<>();

|**Method**|**Description**|
|---|---|
|`put(K key, V value)`|Inserts a key-value pair into the map.|
|`get(Object key)`|Returns the value associated with the specified key.|
|`remove(Object key)`|Removes the entry for the specified key.|
|`containsKey(Object key)`|Returns `true` if the map contains the specified key.|
|`size()`|Returns the number of key-value pairs in the map.|
|`keySet()`|Returns a `Set` view of all keys in the map.|
|`values()`|Returns a `Collection` view of all values in the map.|

---

### Code Example: Managing User Ages


``` java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        // Create a HashMap: Key is String (Name), Value is Integer (Age)
        HashMap<String, Integer> people = new HashMap<>();

        // 1. Adding data
        people.put("Alice", 25);
        people.put("Bob", 30);
        people.put("Charlie", 35);

        // 2. Accessing data
        System.out.println("Alice's age: " + people.get("Alice"));

        // 3. Updating data (overwrites the old value)
        people.put("Alice", 26);

        // 4. Checking existence
        if (people.containsKey("Bob")) {
            System.out.println("Bob is in the system.");
        }

        // 5. Removing data
        people.remove("Charlie");

        System.out.println(people); // Output: {Bob=30, Alice=26}
    }
}
```

---

### How it Works (Hashing & Collisions)

When you call `put(key, value)`, Java performs the following steps:

1. **Hash Code:** It calculates a "hash" of the key.
    
2. **Index:** It uses that hash to find a specific "bucket" (index in an internal array).
    
3. **Collision Handling:** If two different keys end up in the same bucket (a **collision**), Java stores them in a **LinkedList** (or a **Red-Black Tree** in newer Java versions) at that index.
    

---

### Comparison: HashMap vs. Other Maps

|**Feature**|**HashMap**|**LinkedHashMap**|**TreeMap**|
|---|---|---|---|
|**Ordering**|Random / None|Insertion Order|Sorted (by Keys)|
|**Speed**|Fastest|Slightly slower|Slower ($O(\log n)$)|
|**Null Keys**|Allowed|Allowed|Not Allowed|

# [[Iteration in HashMap]]