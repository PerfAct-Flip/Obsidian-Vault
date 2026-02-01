A **HashSet** is a collection in Java that is used to store unique elements. It is part of the `java.util` package and implements the `Set` interface.

The most important thing to remember about a `HashSet` is that it **does not allow duplicate values** and **does not guarantee any specific order** of elements.

---

### How it Works: The "Hashing" Mechanism

Behind the scenes, a `HashSet` uses a `HashMap` to store its data. When you add an element, Java uses a formula called **Hashing** to convert the element into an integer (hash code), which determines exactly where that element is stored in memory (the "bucket").

- **No Duplicates:** Before adding an element, Java checks if its hash code already exists. If it does, and the elements are equal, the new one isn't added.
    
- **Null Values:** It allows a single `null` value.
    
- **Performance:** It offers constant-time performance ($O(1)$) for basic operations like adding, removing, and searching.
    

---

### Key Methods of HashSet

|**Method**|**Description**|
|---|---|
|`add(E e)`|Adds the element if it is not already present.|
|`contains(Object o)`|Returns `true` if the set contains the element.|
|`remove(Object o)`|Removes the specified element if it exists.|
|`clear()`|Removes all elements from the set.|
|`size()`|Returns the number of elements in the set.|
|`isEmpty()`|Returns `true` if the set contains no elements.|

---

### Code Example: Removing Duplicates


``` java
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashSet<String> cars = new HashSet<>();

        // Adding elements
        cars.add("Volvo");
        cars.add("BMW");
        cars.add("Ford");
        cars.add("BMW"); // Duplicate - will be ignored
        cars.add("Mazda");

        // Checking if an item exists
        System.out.println(cars.contains("Mazda")); // Output: true

        // Removing an item
        cars.remove("Volvo");

        // Printing the set
        System.out.println(cars); 
        // Output might be: [Ford, BMW, Mazda] (Order is not guaranteed)
    }
}
```

---

### Comparison: HashSet vs. Others

|**Feature**|**HashSet**|**LinkedHashSet**|**TreeSet**|
|---|---|---|---|
|**Ordering**|No order guaranteed|Insertion order|Natural sorted order|
|**Performance**|Fastest ($O(1)$)|Slightly slower than HashSet|Slower ($O(\log n)$)|
|**Implementation**|Hash Table|Hash Table + Linked List|Red-Black Tree|

---

### When to use HashSet?

- When you need to store a list of items where **uniqueness** is the top priority (like User IDs or unique Email addresses).
    
- When the **order of items doesn't matter**.
    
- When you need the **fastest possible performance** for searching and inserting.
    

# [[Iterator]]