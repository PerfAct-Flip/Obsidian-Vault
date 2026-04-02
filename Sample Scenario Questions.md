
---

## **Question 1: The Cafeteria Queue (Easy)**

**Challenge Name:** `TokenGenerator`

### **Problem Statement**

In your college cafeteria, the billing system is broken. The manager wants a program that automatically assigns a "Priority Token" to students.

- If a student's ID number is **even**, they get a **"Silver"** token.
    
- If a student's ID number is **odd**, they get a **"Blue"** token.
    
- However, if the ID number is a multiple of **10**, they are a club member and get a **"Gold"** token.
    

**Task:** Write a program that takes an integer (Student ID) and prints the correct token type.

### **Input Format**

A single integer representing the Student ID.

### **Constraints**

$1 \le ID \le 10^5$

### **Output Format**

Print exactly one word: `Gold`, `Silver`, or `Blue`.

### **Test Cases**

|**Input**|**Expected Output**|**Logic**|
|---|---|---|
|`20`|`Gold`|Multiple of 10 takes priority.|
|`14`|`Silver`|Even number.|
|`7`|`Blue`|Odd number.|

---

## **Question 2: The Library Late Fee (Easy-Medium)**

**Challenge Name:** `LibraryFine`

### **Problem Statement**

The college library has a new fine policy to encourage students to return books on time.

1. If the book is returned within **5 days**, the fine is **₹2 per day**.
    
2. If the book is returned between **6 and 10 days**, the fine is **₹5 per day**.
    
3. If the book is returned after **10 days**, it is a flat fine of **₹100**.
    

**Task:** Given the number of days a book is overdue, calculate the total fine amount.

### **Input Format**

A single integer $D$ (number of days).

### **Constraints**

$0 \le D \le 100$

### **Output Format**

Print the total fine as an integer.

### **Test Cases**

|**Input**|**Expected Output**|**Logic**|
|---|---|---|
|`3`|`6`|$3 \times 2 = 6$|
|`7`|`35`|$7 \times 5 = 35$|
|`12`|`100`|Flat fee for $>10$ days.|

---

## **Question 3: The Secret Message (Medium)**

**Challenge Name:** `VowelShift`

### **Problem Statement**

Two friends, Rahul and Diya, want to send secret notes in class. They decide on a simple code: **Remove all vowels (a, e, i, o, u)** from a word to make it "hidden."

**Task:** Write a program that takes a string (a single word) and prints the string with all vowels removed. The system should handle both uppercase and lowercase vowels.

### **Input Format**

A single string $S$.

### **Constraints**

$1 \le |S| \le 50$ (Length of string).

### **Output Format**

The modified string without vowels.

### **Test Cases**

|**Input**|**Expected Output**|**Logic**|
|---|---|---|
|`HackerRank`|`Hckrnk`|a and e removed.|
|`ACM`|`CM`|A removed.|
|`BCD`|`BCD`|No vowels to remove.|

---
