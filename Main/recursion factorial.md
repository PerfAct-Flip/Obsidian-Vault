

### **Code:**

```c
#include <stdio.h>

// Function to calculate factorial using recursion
long long factorial_recursive(int n) {
    if (n == 0 || n == 1)
        return 1;
    return n * factorial_recursive(n - 1);
}

// Function to calculate factorial using a loop (iterative)
long long factorial_iterative(int n) {
    long long fact = 1;
    for (int i = 1; i <= n; i++) {
        fact *= i;
    }
    return fact;
}

int main() {
    int num;
    
    // Input from user
    printf("Enter a number: ");
    scanf("%d", &num);

    if (num < 0) {
        printf("Factorial of a negative number is not defined.\n");
    } else {
        printf("Factorial (Recursive) of %d: %lld\n", num, factorial_recursive(num));
        printf("Factorial (Iterative) of %d: %lld\n", num, factorial_iterative(num));
    }

    return 0;
}
```

### **Explanation:**

1. **Recursive Function (`factorial_recursive`)**:
    
    - If `n == 0` or `n == 1`, return `1` (base case).
    - Otherwise, return `n * factorial(n-1)`.
2. **Iterative Function (`factorial_iterative`)**:
    
    - Uses a loop to multiply numbers from `1` to `n`.
3. **Main Function**:
    
    - Takes input from the user.
    - Handles negative numbers by displaying an error message.
    - Calls both functions and prints the results.

### **Example Output:**

```
Enter a number: 5
Factorial (Recursive) of 5: 120
Factorial (Iterative) of 5: 120
```

Let me know if you need modifications! 🚀