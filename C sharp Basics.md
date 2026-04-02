
---


---

## 📘 C# Basics – Summary Notes

### 🔷 **1. Printing Output**

```csharp
Console.WriteLine("HelloWorld");
```

---

### 🔢 **2. Numeric Data Types**

|Data Type|Example|Note|
|---|---|---|
|`int`|`int num = 2;`|Default integer (Int32)|
|`long`|`long longNum = 20000000000L;`|Use `L` for long (Int64)|
|`double`|`double val = 20.4D;`|Use `D` for precision|
|`float`|`float val = 0.3F;`|Use `F` suffix|
|`decimal`|`decimal val = 2.5M;`|Use `M` suffix for money or high precision|

#### ✅ Max/Min Values

```csharp
Console.WriteLine(int.MaxValue);
Console.WriteLine(int.MinValue);
```

---

### 🔒 **3. Constants**

```csharp
const int maxLen = 20;
const double ratio = maxLen / 100D;
```

---

### 🔄 **4. Type Conversion**

```csharp
string ageStr = "20";
int age = Convert.ToInt32(ageStr);
```

---

### 🧑‍💻 **5. User Input**

```csharp
Console.WriteLine("Enter name:");
string name = Console.ReadLine();
Console.WriteLine("Name: " + name);
```

---

### 🧠 **6. Conditional Statements**

```csharp
if (condition) {
  // ...
} else if (otherCondition) {
  // ...
} else {
  // ...
}
```

---

### 🔁 **7. Switch Case**

```csharp
switch (day) {
  case 1:
    Console.WriteLine("1");
    break;
  default:
    Console.WriteLine("Default");
    break;
}
```

---

### 🔄 **8. Loops**

- `for`, `while` loops can be used normally (not implemented in the example but mentioned).
    

---

### ❓ **9. Ternary Operator**

```csharp
string result = age != 0 ? "valid" : "invalid";
```

---

### 💰 **10. Numeric Formatting**

```csharp
double val = 1000D / 34.45D;
Console.WriteLine(string.Format("{0:0.00}", val));  // 2 decimal places
Console.WriteLine(string.Format("{0:0.0#}", val));  // removes trailing zero if not needed
```

---

### 💵 **11. Currency Formatting**

```csharp
double money = -10D / 3D;

Console.WriteLine(money.ToString("C")); // Default currency (based on system locale)
Console.WriteLine(money.ToString("C0")); // No decimal places
Console.WriteLine(money.ToString("C2")); // 2 decimal places

// With specific culture:
using System.Globalization;
Console.WriteLine(money.ToString("C", CultureInfo.CreateSpecificCulture("en-US")));
```

---


## 📘 C# Concepts – Part 2

---

### 🔹 **1. `TryParse()` Method**

Safely converts a string to a number **without throwing exceptions**.

```csharp
string input = Console.ReadLine();
int number;
bool success = int.TryParse(input, out number);

if (success)
{
    Console.WriteLine("Conversion successful: " + number);
}
else
{
    Console.WriteLine("Conversion failed, default: " + number); // default is 0
}
```

🟢 **Why use TryParse?**

- Prevents exceptions if input is invalid
    
- Great for validating user input
    

---

### 🧠 **2. Exercise: Times Table**

💡 Prompt the user for a number, then print that number's multiplication table using a loop.

```csharp
Console.WriteLine("Enter a number for times table:");
int num = Convert.ToInt32(Console.ReadLine());

for (int i = 1; i <= 10; i++)
{
    Console.WriteLine($"{num} x {i} = {num * i}");
}
```

---

### 🎮 **3. Exercise: FizzBuzz**

Classic loop-based logic challenge:

```csharp
Console.WriteLine("Enter a number:");
int limit = Convert.ToInt32(Console.ReadLine());

for (int i = 1; i <= limit; i++)
{
    if (i % 3 == 0 && i % 5 == 0)
        Console.WriteLine("FizzBuzz");
    else if (i % 3 == 0)
        Console.WriteLine("Fizz");
    else if (i % 5 == 0)
        Console.WriteLine("Buzz");
    else
        Console.WriteLine(i);
}
```

---

### ✏️ **4. Verbatim String Literals (`@`)**

Allows strings to span multiple lines or ignore escape characters.

```csharp
string name = "soham";
Console.WriteLine($"Your name: {name}");  // Interpolated string

Console.WriteLine(@"Your name: {name}");  // Verbatim string - won't replace {name}
```

🧵 **Verbatim String Notes:**

- Starts with `@`
    
- Treats backslashes (`\`) as literal characters
    
- Useful for file paths or disabling escape sequences
    

Example:

```csharp
string path = @"C:\Users\Soham\Documents";
```

---

### 📌 Summary

|Concept|Purpose|
|---|---|
|`TryParse()`|Safe string-to-int conversion|
|Times Table Exercise|Practice with loops and input|
|FizzBuzz|Classic logic challenge|
|`@` Strings|Verbatim strings, no escaping needed|

---

