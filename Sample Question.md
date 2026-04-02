### **Question 1: Predict the Output (Integer Arithmetic)**

**Challenge Name:** The Modulo Mystery

**Problem Statement:** What is the exact output of the following C++ code?

C++

```
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 3;
    int res = a % b + a / b;
    cout << res;
    return 0;
}
```

**Input Format:** No input.

**Output Format:** Print a single integer representing the final value of `res`.

**Test Case (Expected Output):** `4`

_(Logic: 10 % 3 = 1; 10 / 3 = 3; 1 + 3 = 4)_