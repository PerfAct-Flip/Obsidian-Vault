To iterate through a **HashMap**, you have a few options depending on whether you need just the keys, just the values, or both.

In modern Java, the most common way is using the `entrySet()` or the `forEach` lambda.

---

### 1. Using `entrySet()` (Most Efficient)

This is the best way to get both the **Key** and the **Value** at the same time. It returns a set of `Map.Entry` objects.


``` java
for (Map.Entry<String, Integer> entry : people.entrySet()) {
    System.out.println("Name: " + entry.getKey() + ", Age: " + entry.getValue());
}
```

### 2. Using `forEach` with Lambda (Java 8+)

This is the most concise and readable method.


``` java
people.forEach((name, age) -> {
    System.out.println(name + " is " + age + " years old.");
});
```

---

### Internal Structure: How HashMap stores data

When you look at a HashMap internally, it's essentially an array of **Buckets**. Each bucket can hold one or more entries (if there is a collision).

---

### Comparison: EntrySet vs. KeySet

|**Method**|**Returns**|**Best Use Case**|
|---|---|---|
|**`entrySet()`**|Both Key & Value|When you need to process both pieces of data together.|
|**`keySet()`**|Just the Keys|When you only care about the labels (e.g., a list of usernames).|
|**`values()`**|Just the Values|When you only care about the data (e.g., calculating the average age).|

---

### Summary of the "Collection" Series

We have covered a lot of ground! Here is how they all fit together:

- **ArrayList:** Your go-to for ordered, index-based lists.
    
- **HashSet:** Use it when you need a "bag" of unique items.
    
- **HashMap:** Use it for fast lookups using a specific key.
    
- **Iterator:** Use it to safely move through and modify these collections.
    

Would you like to see a complex example where we combine a **HashMap** with an **ArrayList** (e.g., a map where one key points to a list of values)?