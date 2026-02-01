**Java Collections Framework**
---

## 🟢 Core Methods of the Collection Interface

These methods are inherited by most sub-interfaces (List, Set, Queue) and are essential for manipulating data.

|**Method**|**Description**|
|---|---|
|`add(E e)`|Inserts an element into the collection.|
|`size()`|Returns the number of elements in the collection.|
|`remove(Object o)`|Removes a specific element if it exists.|
|`iterator()`|Returns an iterator to loop through the collection.|
|`addAll(Collection c)`|Adds all elements from another collection.|
|`removeAll(Collection c)`|Removes all elements contained in the specified collection.|
|`clear()`|Removes all elements from the collection.|

---

## 🟦 Hierarchy of Interfaces & Implementations

### 1. List Interface

_Ordered collections that allow duplicate elements._

- **[[ArrayList]]:** Best for fast iteration and random access (index-based).
    
- **LinkedList:** Best for frequent insertions and deletions (also implements Queue).
    
- **Vector:** Legacy class; synchronized (thread-safe) version of ArrayList.
    
    - **Stack:** A subclass of Vector representing a Last-In-First-Out (LIFO) stack.
        

### 2. Queue Interface

_Designed for holding elements prior to processing (typically FIFO)._

- **PriorityQueue:** Elements are ordered based on their natural ordering or a custom comparator.
    
- **LinkedList:** Can be used as a standard Queue.
    
- **Deque (Double Ended Queue):** Supports element insertion/removal at both ends.
    
    - **ArrayDeque:** A faster, resizable-array implementation of Deque.
        

### 3. Set Interface

_Collections that contain no duplicate elements._

- **[[HashSet]]:** Backed by a hash table; no guarantee of iteration order.
    
- **LinkedHashSet:** Maintains a doubly-linked list to preserve insertion order.
    
- **SortedSet (Interface):** A set that guarantees elements are in ascending order.
    
    - **TreeSet:** Implementation of SortedSet; uses a Red-Black tree structure.
        

---

## 🟧 Map Interface

_Objects that map keys to values; cannot contain duplicate keys._

- **[[HashMap]]:** Stores key-value pairs; no specific order.
    
- **LinkedHashMap:** Maintains insertion order of the keys.
    
- **Hashtable:** Legacy class; synchronized and does not allow null keys/values.
    
- **SortedMap (Interface):** Maps keys in a sorted order.
    
    - **TreeMap:** Implementation of SortedMap; elements are sorted by key.
        

---
