**JavaScript forEach(), map(), filter(), Destructuring, Spread & Rest Operators - Quick Notes**

### **forEach() Method**

#### **Definition**

- `forEach()` is used to iterate over elements in an array.
- Executes a function once for each array element.
- **Does not return a new array** (use `map()` if needed).
- **Cannot be stopped early** (use `for...of` or `some()` if required).

#### **Syntax**

```javascript
array.forEach((element, index, array) => {
    // Code to execute for each element
});
```

#### **Examples**

##### **Basic Usage**

```javascript
const numbers = [1, 2, 3, 4];
numbers.forEach(num => {
    console.log(num * 2);
});
// Output: 2, 4, 6, 8
```

##### **Using Index**

```javascript
const fruits = ["Apple", "Banana", "Cherry"];
fruits.forEach((fruit, index) => {
    console.log(`${index}: ${fruit}`);
});
// Output:
// 0: Apple
// 1: Banana
// 2: Cherry
```

---

### **map() Method**

#### **Definition**

- `map()` creates a new array with the results of calling a provided function on every element.
- **Returns a new array** (does not modify the original array).
- Ideal for **transforming** data.

#### **Syntax**

```javascript
const newArray = array.map((element, index, array) => {
    return element * 2;
});
```

#### **Examples**

##### **Basic Usage**

```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2);
console.log(doubled);
// Output: [2, 4, 6, 8]
```

---

### **filter() Method**

#### **Definition**

- `filter()` creates a new array with elements that pass a given condition.
- **Returns a new array** (does not modify the original array).
- Used for **extracting** specific elements from an array.

#### **Syntax**

```javascript
const newArray = array.filter((element, index, array) => {
    return condition;
});
```

#### **Examples**

##### **Basic Usage**

```javascript
const numbers = [1, 2, 3, 4, 5, 6];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);
// Output: [2, 4, 6]
```

---

### **Destructuring in JavaScript**

#### **Definition**

- Destructuring allows unpacking values from arrays or properties from objects into distinct variables.
- Makes code more readable and concise.

#### **Array Destructuring**

```javascript
const numbers = [10, 20, 30];
const [first, second, third] = numbers;
console.log(first, second, third);
// Output: 10 20 30
```

##### **Using Rest Operator**

```javascript
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;
console.log(first, second, rest);
// Output: 1 2 [3, 4, 5]
```

#### **Object Destructuring**

```javascript
const person = { name: "Alice", age: 25, city: "New York" };
const { name, age, city } = person;
console.log(name, age, city);
// Output: Alice 25 New York
```

---

### **Spread Operator (`...`)**

#### **Definition**

- Expands elements of an array or object.
- Used for copying, merging, or passing elements.

#### **Examples**

##### **Copying Arrays**

```javascript
const numbers = [1, 2, 3];
const newNumbers = [...numbers];
console.log(newNumbers);
// Output: [1, 2, 3]
```

##### **Merging Arrays**

```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];
const merged = [...arr1, ...arr2];
console.log(merged);
// Output: [1, 2, 3, 4]
```

##### **Copying Objects**

```javascript
const person = { name: "Alice", age: 25 };
const newPerson = { ...person, city: "New York" };
console.log(newPerson);
// Output: { name: "Alice", age: 25, city: "New York" }
```

---

### **Rest Operator (`...`)**

#### **Definition**

- Gathers multiple elements into an array or object.
- Used in function parameters and destructuring.

#### **Examples**

##### **Function Parameters**

```javascript
function sum(...numbers) {
    return numbers.reduce((acc, num) => acc + num, 0);
}
console.log(sum(1, 2, 3, 4));
// Output: 10
```

##### **Object Rest Destructuring**

```javascript
const person = { name: "Alice", age: 25, city: "New York" };
const { name, ...details } = person;
console.log(details);
// Output: { age: 25, city: "New York" }
```

---

### **Key Differences: forEach() vs map() vs filter()**

|Feature|forEach()|map()|filter()|
|---|---|---|---|
|Return Value|Undefined|New Array|New Array|
|Modifies Original?|Yes|No|No|
|Use Case|Iteration|Transformation|Extraction|
|Supports Chaining|No|Yes|Yes|

---

### **Use Cases:**

✅ `forEach()` → Logging, modifying elements, side effects.  
✅ `map()` → Creating a new transformed array.  
✅ `filter()` → Selecting specific elements from an array.  
✅ **Destructuring** → Extracting values from objects and arrays efficiently.  
✅ **Spread (`...`)** → Copying, merging, expanding elements.  
✅ **Rest (`...`)** → Collecting values in functions or objects.

---