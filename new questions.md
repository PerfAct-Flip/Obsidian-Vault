To ensure your **Mind Sprint** event is professional and the grading is automated correctly, here is the complete data for each of the 5 Parameterized Output challenges. You can copy-paste these directly into the HackerRank "Create Challenge" fields.

---

### **Question 1: Step-Up Multiplier**

- **Description:** Calculate a robot's final position using alternating arithmetic rules.
    
- **Problem Statement:** A robot starts at **position 1** and moves through $N$ steps (from $i = 1$ to $N$).
    
    For each step $i$:
    
    - If the step number $i$ is **odd**, the robot adds $i$ to its current position.
        
    - If the step number $i$ is **even**, the robot multiplies its current position by $i$.
        
    
    Write a program to determine the robot's final position after $N$ steps.
    
- **Input Format:** A single integer $N$.
    
- **Output Format:** A single integer representing the final position.
    
- **Constraints:** $1 \le N \le 15$
    
- **Tags:** `Basic-Programming`, `Loops`, `Conditional-Logic`
    
- **Test Cases:**
    
    - **Sample Case:** Input: `3` | Output: `7` _(Logic: Start 1 $\xrightarrow{+1}$ 2 $\xrightarrow{*2}$ 4 $\xrightarrow{+3}$ 7)_
        
    - **Hidden Case 1:** Input: `5` | Output: `65`
        
    - **Hidden Case 2:** Input: `1` | Output: `2`
        

---

### **Question 2: Discount Eraser**

- **Description:** Determine the total bill for a store with a resetting discount glitch.
    
- **Problem Statement:** A shop sells $N$ items, each with a base price of **₹100**.
    
    - The discount starts at ₹5 for the first item and increases by ₹5 for every subsequent item ($5, 10, 15...$).
        
    - **The Glitch:** If the item number $i$ is a multiple of **3**, the discount resets to **₹0** for that specific item and starts increasing again from the next item.
        
    
    Calculate the total bill (Sum of [Base Price - Discount]) for $N$ items.
    
- **Input Format:** A single integer $N$.
    
- **Output Format:** A single integer representing the total price.
    
- **Constraints:** $1 \le N \le 100$
    
- **Tags:** `Arithmetic`, `Modulo-Operator`, `Implementation`
    
- **Test Cases:**
    
    - **Sample Case:** Input: `3` | Output: `285` _(Logic: [100-5] + [100-10] + [100-0])_
        
    - **Hidden Case 1:** Input: `5` | Output: `475`
        
    - **Hidden Case 2:** Input: `6` | Output: `575`
        

---

### **Question 3: Alternating Sum**

- **Description:** Calculate the sum of an array where even-indexed elements are added and odd ones are subtracted.
    
- **Problem Statement:** You are given an array of $N$ integers. Your task is to calculate the **Alternating Sum** based on the **index of each element**:
    
    - **Add** the element to the total sum if its index is even ($0, 2, 4 \dots$).
        
    - **Subtract** the element from the total sum if its index is odd ($1, 3, 5 \dots$).
        
    
    Output the final result.
    
- **Input Format:** 1. First line: Integer $N$.
    
    2. Second line: $N$ space-separated integers representing the array.
    
- **Output Format:** A single integer representing the alternating sum.
    
- **Constraints:** $1 \le N \le 1000$
    
- **Tags:** `Arrays`, `Looping`, `Math`
    
- **Test Cases:**
    
    - **Sample Case:** Input: `4 \n 10 20 30 40` | Output: `-20` _(Logic: 10 - 20 + 30 - 40)_
        
    - **Hidden Case 1:** Input: `3 \n 5 5 5` | Output: `5`
        
    - **Hidden Case 2:** Input: `1 \n 100` | Output: `100`
        

---

### **Question 4: ASCII Character Shift**

- **Description:** Shift every character in a string forward based on its index position.
    
- **Problem Statement:** To encode a word of length $N$, every character in the string is shifted forward in the ASCII table by its **index position**:
    
    - Index 0: No shift.
        
    - Index 1: Shift forward by 1 ('a' $\rightarrow$ 'b', 'b' $\rightarrow$ 'c').
        
    - Index $i$: Shift forward by $i$.
        
    
    Given the string length $N$ and the word, output the encrypted string.
    
- **Input Format:** 1. First line: Integer $N$.
    
    2. Second line: A string of length $N$.
    
- **Output Format:** The modified string without any spaces.
    
- **Constraints:** $1 \le |S| \le 50$ (String contains only lowercase letters)
    
- **Tags:** `Strings`, `Character-Arithmetic`, `Encryption`
    
- **Test Cases:**
    
    - **Sample Case:** Input: `3 \n abc` | Output: `ace` _(Logic: a+0, b+1, c+2)_
        
    - **Hidden Case 1:** Input: `5 \n hello` | Output: `hfnos`
        
    - **Hidden Case 2:** Input: `4 \n test` | Output: `tfuv`
        

---

### **Question 5: Capped Sum**

- **Description:** Calculate the sum of the first N natural numbers with a specific "Cap" limit.
    
- **Problem Statement:** Write a program that takes two space-separated integers, $N$ and $K$.
    
    1. Calculate the sum of the first $N$ natural numbers ($1 + 2 + \dots + N$).
        
    2. **The Constraint:** If the **running sum** ever reaches or exceeds the value $K$, the final result must immediately be returned as $K$.
        
    
    Output the final sum.
    
- **Input Format:** Two space-separated integers $N$ and $K$.
    
- **Output Format:** A single integer.
    
- **Constraints:** $1 \le N \le 100$, $1 \le K \le 1000$
    
- **Tags:** `Conditionals`, `Loops`, `Summation`
    
- **Test Cases:**
    
    - **Sample Case:** Input: `5 10` | Output: `10` _(Logic: Sum 1+2+3+4 = 10; since it reached 10, it stops before adding 5)_
        
    - **Hidden Case 1:** Input: `3 10` | Output: `6`
        
    - **Hidden Case 2:** Input: `10 50` | Output: `50`
        

---

### **Admin Tip: How to Grade these Properly**

Since you are the Head of the Tech Society, ensure your technical team uses the **"Seller's Solution"** or **"Editorial Solution"** feature on HackerRank. This ensures that even if students try to print a single number, they will fail the other **hidden test cases**, which will correctly judge their logic.

**Would you like me to provide the "Seller's Solution" code in C++ for all these so you have the master key ready?**


[[answers]]