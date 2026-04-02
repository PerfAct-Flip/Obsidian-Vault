using tsc app.ts in terminal to run code and compile it to js
using tsc --init generates tsconfig.json

tsc --watch 
will compile file automatically

---

# Basic Types
### **Primitives and References in TypeScript**

In TypeScript (just like in JavaScript), data types are categorized into **Primitive Types** and **Reference Types**.

---

## **1. Primitive Types**

Primitives are **immutable** and stored directly in memory. They hold **actual values** and are compared by value.

### **Primitive Types in TypeScript**

|Type|Description|Example|
|---|---|---|
|`number`|Represents numeric values (integers, floats, etc.)|`let age: number = 25;`|
|`string`|Represents textual values|`let name: string = "Alice";`|
|`boolean`|Represents `true` or `false` values|`let isActive: boolean = true;`|
|`null`|Represents an intentional absence of value|`let empty: null = null;`|
|`undefined`|Represents an uninitialized variable|`let notAssigned: undefined;`|
|`bigint`|Used for very large numbers|`let bigNumber: bigint = 9007199254740991n;`|
|`symbol`|Unique and immutable values used as object keys|`let sym: symbol = Symbol("id");`|

### **Example of Primitive Behavior**

```typescript
let x = 10;
let y = x;  // Copying value

y = 20;  // Changing y doesn't affect x

console.log(x); // 10
console.log(y); // 20
```

Since `x` and `y` are primitive types, `y` gets a **copy** of `x`, so modifying `y` does not affect `x`.

---

## **2. Reference Types**

Reference types **store references (memory addresses)** instead of actual values. They are **mutable** and compared by reference.

### **Common Reference Types in TypeScript**

|Type|Description|Example|
|---|---|---|
|`object`|Represents objects with properties|`let user = { name: "Alice", age: 25 };`|
|`array`|Represents a list of values|`let nums: number[] = [1, 2, 3];`|
|`function`|Represents functions as first-class objects|`const greet = () => "Hello";`|
|`class`|Represents object-oriented classes|`class Person {}`|

### **Example of Reference Behavior**

```typescript
let obj1 = { name: "Alice" };
let obj2 = obj1;  // Copying reference

obj2.name = "Bob";  // Changing obj2 affects obj1

console.log(obj1.name); // "Bob"
console.log(obj2.name); // "Bob"
```

Since `obj1` and `obj2` **refer to the same memory address**, modifying `obj2` also changes `obj1`.

---

## **3. Key Differences: Primitives vs References**

|Feature|Primitive Types|Reference Types|
|---|---|---|
|**Storage**|Stored directly in memory (stack)|Stores a reference (heap)|
|**Mutability**|Immutable (new value creates a new copy)|Mutable (changes affect all references)|
|**Comparison**|Compared by **value**|Compared by **reference**|
|**Assignment**|Creates a copy|Copies reference (not value)|

---

## **4. Cloning Reference Types to Avoid Mutation**

To prevent modifying the original object, you can **clone** it.

### **Using `Object.assign()`**

```typescript
let obj1 = { name: "Alice" };
let obj2 = Object.assign({}, obj1);

obj2.name = "Bob";

console.log(obj1.name); // "Alice" (Unchanged)
console.log(obj2.name); // "Bob"
```

### **Using Spread Operator (`...`)**

```typescript
let obj1 = { name: "Alice" };
let obj2 = { ...obj1 };

obj2.name = "Bob";

console.log(obj1.name); // "Alice" (Unchanged)
console.log(obj2.name); // "Bob"
```

### **Deep Copy (For Nested Objects)**

Shallow copies (like `Object.assign()` and spread operator) only copy **top-level properties**. For deep cloning, use:

```typescript
let obj1 = { name: "Alice", address: { city: "NY" } };
let obj2 = JSON.parse(JSON.stringify(obj1));

obj2.address.city = "LA";

console.log(obj1.address.city); // "NY" (Original remains unchanged)
console.log(obj2.address.city); // "LA"
```

---

### **5. When to Use Which Type?**

- **Use primitives** when storing **simple values** (numbers, strings, booleans) that don’t need to be modified.
- **Use reference types** for **collections, complex structures, and when mutability is needed**.

---

### **6. Summary**

|Concept|Primitive Types|Reference Types|
|---|---|---|
|Stored in|Stack|Heap|
|Mutable?|❌ No|✅ Yes|
|Comparison|By Value|By Reference|
|Example Types|`string`, `number`, `boolean`|`object`, `array`, `function`|

---

Let me know if you need more examples! 🚀
