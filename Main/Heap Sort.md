
Imagine you are **building a sandcastle pyramid**, but you want the **biggest** sand bucket at the bottom and the **smallest** at the top.

Here’s how you do it:

1. First, **arrange** all the buckets into a **big pyramid shape** (called a **heap**).
2. The **biggest bucket** (largest number) always comes to the **top** of the pyramid.
3. Remove the **biggest bucket**, put it in its correct position, and **rearrange the remaining buckets** into a new pyramid.
4. Repeat the process until all buckets are arranged in order from **smallest to largest**.

This is **Heap Sort**—it **builds** a special pyramid (heap) and repeatedly **removes the biggest element** to sort the list.

---

### **Heap Sort Algorithm** 📝

1. **Build a max heap** (biggest number on top).
2. **Swap the root (largest) with the last element** and reduce heap size.
3. **Heapify** (rearrange) the remaining elements into a valid heap.
4. Repeat until all elements are sorted.

---

### **Heap Sort Code in C** 💻

```c
#include <stdio.h>

// Function to swap two numbers
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Function to heapify a subtree rooted at index i
void heapify(int arr[], int n, int i) {
    int largest = i;   // Initialize largest as root
    int left = 2 * i + 1;  // Left child index
    int right = 2 * i + 2; // Right child index

    // If left child is larger than root
    if (left < n && arr[left] > arr[largest])
        largest = left;

    // If right child is larger than largest so far
    if (right < n && arr[right] > arr[largest])
        largest = right;

    // If largest is not root, swap and heapify again
    if (largest != i) {
        swap(&arr[i], &arr[largest]);
        heapify(arr, n, largest);
    }
}

// Function to perform Heap Sort
void heapSort(int arr[], int n) {
    // Build a max heap (rearrange array)
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Extract elements from heap one by one
    for (int i = n - 1; i > 0; i--) {
        swap(&arr[0], &arr[i]);  // Move current root to end
        heapify(arr, i, 0);  // Heapify the reduced heap
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
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original Array: ");
    printArray(arr, n);

    heapSort(arr, n);

    printf("Sorted Array: ");
    printArray(arr, n);

    return 0;
}
```

---

### **Time Complexity** ⏳

- **Best Case:** O(n log n)
- **Average Case:** O(n log n)
- **Worst Case:** O(n log n)

### **Space Complexity** 🗃️

- O(1) (Sorts in-place, no extra memory needed)

---

### **Where is it useful?**

✅ **Faster than Bubble, Selection, and Insertion Sort**  
✅ **Good when memory usage needs to be minimal**  
✅ **Works well for large datasets**  
🚫 **Not stable (order of equal elements may change)**

Would you like a step-by-step visualization? 🚀