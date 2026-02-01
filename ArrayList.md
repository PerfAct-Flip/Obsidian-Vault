An **ArrayList** is one of the most commonly used data structures in Java. It is part of the `java.util` package and implements the `List` interface.

Think of it as a **dynamic array**: unlike a standard array which has a fixed size, an `ArrayList` automatically grows and shrinks as you add or remove elements.

---

### How it Works

- **Internal Storage:** It uses a regular array behind the scenes.
    
- **Resizing:** When the array is full, it creates a new, larger array (usually 1.5x the size) and copies the old elements over.
    
- **Access:** It allows for fast, random access to elements using an index.
    

---

### Essential ArrayList Methods

To use these methods, you first initialize your list:

ArrayList<String> list = new ArrayList<>();

#### 1. Adding Elements

- `add(E element)`: Appends the element to the end of the list.
    
- `add(int index, E element)`: Inserts the element at a specific position.
    
- `addAll(Collection c)`: Appends all elements from another collection.
    

#### 2. Accessing & Modifying

- `get(int index)`: Returns the element at the specified index.
    
- `set(int index, E element)`: Replaces the element at the index with a new one.
    
- `size()`: Returns the number of elements in the list.
    

#### 3. Removing Elements

- `remove(int index)`: Removes the element at the specific index.
    
- `remove(Object o)`: Removes the first occurrence of the specified element.
    
- `clear()`: Removes all elements from the list.
    

#### 4. Searching & Checking

- `contains(Object o)`: Returns `true` if the list contains the element.
    
- `indexOf(Object o)`: Returns the index of the first occurrence (or -1 if not found).
    
- `isEmpty()`: Returns `true` if the list has no elements.
    

---

### Comparison: ArrayList vs. Standard Array

|**Feature**|**Standard Array**|**ArrayList**|
|---|---|---|
|**Size**|Fixed (Static)|Dynamic (Resizable)|
|**Performance**|Faster for basic tasks|Slightly slower due to resizing|
|**Data Types**|Primitives & Objects|Objects only (uses Wrappers for primitives)|
|**Methods**|Very few built-in|Rich set of manipulation methods|

---

### Pro-Tips for Using ArrayLists

- **Performance:** `add()` and `get()` are very fast ($O(1)$). However, inserting or removing elements in the middle of the list is slower ($O(n)$) because all subsequent elements must be shifted.
    
- **Generics:** Always specify the type (e.g., `ArrayList<Integer>`) to ensure type safety and avoid errors at runtime.
    

