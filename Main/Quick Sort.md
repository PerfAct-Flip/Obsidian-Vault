
Imagine you have a pile of **messy books**, and you want to **arrange them by size**. Here’s how Quick Sort works:

1. **Pick one book** (this is called the **pivot**).
2. Move all the **smaller books to the left** and **bigger books to the right**.
3. Now, the pivot is in its **correct position**!
4. Repeat the same process for the **left pile** and **right pile** until everything is sorted.

This method is **super fast** because it quickly breaks the problem into smaller and smaller parts! 🚀

---

### **Quick Sort Algorithm** 📝

1. Pick a **pivot** (usually the last element).
2. Partition the array:
    - Move **smaller** elements to the **left**.
    - Move **larger** elements to the **right**.
3. Recursively repeat **Quick Sort** for the left and right halves.

---

### **Quick Sort Code in C** 💻

```c
#include <stdio.h>

// Function to swap two numbers
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Function to partition the array
int partition(int arr[], int low, int high) {
    int pivot = arr[high];  // Choose the last element as pivot
    int i = low - 1;  // Pointer for smaller element

    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {  // If current element is smaller than pivot
            i++;
            swap(&arr[i], &arr[j]);
        }
    }

    // Place pivot in the correct position
    swap(&arr[i + 1], &arr[high]);
    return i + 1;  // Return pivot index
}

// Quick Sort function
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pivotIndex = partition(arr, low, high);  // Partition the array

        quickSort(arr, low, pivotIndex - 1);  // Sort the left half
        quickSort(arr, pivotIndex + 1, high);  // Sort the right half
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
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original Array: ");
    printArray(arr, n);

    quickSort(arr, 0, n - 1);

    printf("Sorted Array: ");
    printArray(arr, n);

    return 0;
}
```

---

### **Time Complexity** ⏳

- **Best Case:** O(n log n)
- **Average Case:** O(n log n)
- **Worst Case:** O(n²) (If pivot is always the smallest or largest)

### **Space Complexity** 🗃️

- O(log n) (for recursion stack)

---

### **Where is it useful?**

✅ **Super fast for large datasets**  
✅ **Works well when the pivot is chosen wisely**  
🚫 **Bad if the pivot is always the smallest/largest (unbalanced partitioning)**

Would you like an optimized version (like choosing a better pivot)? 🚀