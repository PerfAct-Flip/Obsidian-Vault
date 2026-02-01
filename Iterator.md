	In Java, an **Iterator** is an object used to loop through collections, such as `ArrayList`, `HashSet`, or `LinkedList`. It belongs to the `java.util` package and is part of the Collection Framework.

While you can use a `for-each` loop to read data, an **Iterator** is the only safe way to **modify** a collection (like removing an item) while you are currently looping through it.

---

### How an Iterator Works

Imagine a pointer sitting just before the first element of a list. The Iterator moves this pointer forward one step at a time.

#### The 3 Core Methods:

1. **`hasNext()`**: Returns `true` if there is at least one more element to visit.
    
2. **`next()`**: Returns the next element in the iteration and moves the "pointer" forward.
    
3. **`remove()`**: Removes the last element returned by the iterator from the collection.
    

---

### Basic Example: Iterating through a List



``` java
import java.util.ArrayList;
import java.util.Iterator;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> languages = new ArrayList<>();
        languages.add("Java");
        languages.add("Python");
        languages.add("C++");

        // 1. Get the iterator
        Iterator<String> it = languages.iterator();

        // 2. Loop through the collection
        while(it.hasNext()) {
            System.out.println(it.next());
        }
    }
}
```

---

### Why use an Iterator instead of a For-Loop?

The biggest advantage is the **`remove()`** method. If you try to remove an item from a list while using a standard `for` or `for-each` loop, Java will throw a `ConcurrentModificationException`. An Iterator handles this safely.

#### Example: Removing items during iteration


``` java
ArrayList<Integer> numbers = new ArrayList<>();
numbers.add(10);
numbers.add(5);
numbers.add(15);

Iterator<Integer> it = numbers.iterator();

while(it.hasNext()) {
    Integer i = it.next();
    if(i < 10) {
        it.remove(); // Safely removes '5' from the list
    }
}
System.out.println(numbers); // Output: [10, 15]
```

---

### Iterator vs. ListIterator

Java also provides a specialized version called **`ListIterator`**, which only works on `List` types (ArrayList, LinkedList).

|**Feature**|**Iterator**|**ListIterator**|
|---|---|---|
|**Direction**|Forward only|Forward and Backward|
|**Modification**|Can only remove|Can remove, replace, or add|
|**Scope**|Works with all Collections (Set, List, Queue)|Works only with Lists|

---

### Summary Checklist

- Use `iterator()` to get an instance.
    
- Always check `hasNext()` before calling `next()`.
    
- Use `it.remove()` to delete items during the loop to avoid crashes.
    

Would you like to see how to use a `ListIterator` to traverse a list in reverse order?