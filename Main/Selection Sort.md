
Imagine you are **picking teams for a game**, and you want to arrange players from **shortest to tallest**.

Here’s how you do it:

1. Look at **everyone** and **find the shortest** person.
2. Swap them with the **first person** in the line.
3. Now, ignore the first person (since they are in the correct place) and **find the next shortest** from the remaining group.
4. Swap them with the **second person** in the line.
5. Keep repeating this process until everyone is sorted from shortest to tallest.

This is **Selection Sort**—you repeatedly **select** the smallest number and place it in the right spot.

---

### **Selection Sort Algorithm** 📝

1. Start at the **first position**.
2. Find the **smallest** element in the **remaining** array.
3. Swap it with the **current position**.
4. Move to the **next position** and repeat until the array is sorted.

---

### **Selection Sort Code in C** 💻

```c
#include <stdio.h>

// Function to swap two numbers
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Function to perform Selection Sort
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {  // Move boundary of sorted array
        int minIndex = i;  // Assume the first unsorted element is the smallest

        // Find the smallest element in the remaining array
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }

        // Swap the found smallest element with the first unsorted element
        swap(&arr[minIndex], &arr[i]);
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
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original Array: ");
    printArray(arr, n);

    selectionSort(arr, n);

    printf("Sorted Array: ");
    printArray(arr, n);

    return 0;
}
```

---

### **Time Complexity** ⏳

- **Best Case:** O(n²)
- **Average Case:** O(n²)
- **Worst Case:** O(n²)

### **Space Complexity** 🗃️

- O(1) (Sorts in-place, no extra memory needed)

---

### **Where is it useful?**

✅ **Works well when memory is limited**  
✅ **Simple to implement**  
🚫 **Slow for large datasets**

Would you like an optimized version or a different sorting method? 🚀