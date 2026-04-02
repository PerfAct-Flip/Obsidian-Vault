
Imagine you have a row of **toy cars** lined up from smallest to biggest, but they are all mixed up. You want to **arrange them from smallest to largest**. Here’s how you do it:

1. Start at the **first car** and compare it with the **next car**.
2. If the first car is **bigger**, **swap them**!
3. Move to the next pair and repeat the process.
4. After one full pass, the **biggest car** moves to the end, like a bubble floating to the top.
5. Repeat the process for the remaining cars until everything is sorted!

This is why it’s called **Bubble Sort**—the biggest numbers "bubble" to the top one by one.

---

### **Bubble Sort Algorithm** 📝

1. Start with the first element and compare it with the next.
2. Swap if the first element is bigger.
3. Move to the next element and repeat.
4. After one full pass, the largest element is at the end.
5. Repeat for the remaining elements until everything is sorted.

---

### **Bubble Sort Code in C** 💻

```c
#include <stdio.h>

// Function to swap two numbers
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Bubble Sort Function
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {  // Number of passes
        for (int j = 0; j < n - i - 1; j++) {  // Compare adjacent elements
            if (arr[j] > arr[j + 1]) {  // Swap if out of order
                swap(&arr[j], &arr[j + 1]);
            }
        }
    }
}

// Function to print an array
void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {5, 2, 9, 1, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original Array: ");
    printArray(arr, n);

    bubbleSort(arr, n);

    printf("Sorted Array: ");
    printArray(arr, n);

    return 0;
}
```

---

### **Time Complexity** ⏳

- **Best Case:** O(n) (If already sorted)
- **Average Case:** O(n²)
- **Worst Case:** O(n²)

### **Space Complexity** 🗃️

- O(1) (Sorts in-place, no extra memory needed)

---

This is **simple, easy, and slow**—good for learning but not used in real-world applications. Would you like an optimized version? 🚀