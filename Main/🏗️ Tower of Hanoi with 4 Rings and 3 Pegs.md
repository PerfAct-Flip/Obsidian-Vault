
We have:  
📍 **A (Start peg)**  
📍 **B (Helper peg)**  
📍 **C (Destination peg)**

**Goal:** Move all **4 rings** from A to C following the rules:  
✔ **Move only one ring at a time**  
✔ **A bigger ring can’t sit on a smaller ring**  
✔ **Only the topmost ring of a peg can be moved**

---

### **🛠️ Step-by-Step Solution for 4 Rings**

We follow the same recursive pattern: 1️⃣ **Move 3 smallest rings from A → B**  
2️⃣ **Move the biggest ring from A → C**  
3️⃣ **Move the 3 rings from B → C on top of the biggest ring**

**Visualizing the moves (using numbered rings, where 1 is the smallest and 4 is the biggest):**

```
Step 1: Move ring 1 from A → C  
Step 2: Move ring 2 from A → B  
Step 3: Move ring 1 from C → B  
Step 4: Move ring 3 from A → C  
Step 5: Move ring 1 from B → A  
Step 6: Move ring 2 from B → C  
Step 7: Move ring 1 from A → C  
Step 8: Move ring 4 from A → B  
Step 9: Move ring 1 from C → B  
Step 10: Move ring 2 from C → A  
Step 11: Move ring 1 from B → A  
Step 12: Move ring 3 from C → B  
Step 13: Move ring 1 from A → C  
Step 14: Move ring 2 from A → B  
Step 15: Move ring 1 from C → B  
Step 16: Move ring 4 from B → C  
Step 17: Move ring 1 from B → A  
Step 18: Move ring 2 from B → C  
Step 19: Move ring 1 from A → C  
Step 20: Move ring 3 from B → A  
Step 21: Move ring 1 from C → B  
Step 22: Move ring 2 from C → A  
Step 23: Move ring 1 from B → A  
Step 24: Move ring 3 from A → C  
Step 25: Move ring 1 from A → C  
Step 26: Move ring 2 from A → B  
Step 27: Move ring 1 from C → B  
Step 28: Move ring 3 from C → A  
Step 29: Move ring 1 from B → A  
Step 30: Move ring 2 from B → C  
Step 31: Move ring 1 from A → C  
```

💡 **Total moves for 4 rings = 2⁴ - 1 = 15 moves.**

---

### **💻 C Code for 3 Pegs and 4 Rings**

```c
#include <stdio.h>

// Function to solve Tower of Hanoi
void towerOfHanoi(int n, char from, char to, char aux) {
    if (n == 0) return;  // Base case: No rings to move

    towerOfHanoi(n - 1, from, aux, to);  // Move (n-1) rings to auxiliary peg
    printf("Move ring %d from %c to %c\n", n, from, to); // Move biggest ring
    towerOfHanoi(n - 1, aux, to, from);  // Move smaller rings on top of the big one
}

int main() {
    int n = 4;  // Number of rings
    towerOfHanoi(n, 'A', 'C', 'B');  // A = Start, C = Destination, B = Helper
    return 0;
}
```

---

### **🧐 How This Code Works?**

1. It moves the **top 3 rings** to the helper peg **B**.
2. Moves the **biggest ring** to peg **C**.
3. Moves the **3 rings from B to C** on top of the biggest one.
4. **Recursive function** repeats this for smaller sets of rings.

---

### **🚀 Summary**

✅ **Uses 3 pegs (A, B, C)**  
✅ **Solves for 4 rings in 15 moves**  
✅ **Same recursive logic, just applied for 4 elements**

