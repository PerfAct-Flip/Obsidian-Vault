
Imagine you are **arranging playing cards** in your hand. You pick up one card at a time and place it **in the correct order** among the already sorted cards.

Here’s how you do it:

1. Take the **first card** and hold it. Since it's alone, it's already sorted.
2. Pick the **next card** and compare it with the first card. If it's smaller, move it before the first card.
3. Pick the **third card** and place it in the correct position among the first two.
4. Keep repeating for all cards, **shifting larger cards to the right** to make space for the new card in the correct position.
5. At the end, all cards are sorted! 🎉

---

### **Insertion Sort Algorithm** 📝

1. Start from the **second element** (first one is already sorted).
2. Take the current element and **compare it with elements before it**.
3. Shift elements **to the right** if they are bigger.
4. Place the current element in its **correct position**.
5. Repeat for all elements until the whole array is sorted.

---

### **Insertion Sort Code in C** 💻

```c
#include <stdio.h>

// Function to perform Insertion Sort
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {  // Start from the second element
        int key = arr[i];  // Pick the element to be placed correctly
        int j = i - 1;

        // Shift elements to the right if they are greater than key
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }

        // Place the key in its correct position
        arr[j + 1] = key;
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
    int arr[] = {8, 4, 2, 9, 5};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original Array: ");
    printArray(arr, n);

    insertionSort(arr, n);

    printf("Sorted Array: ");
    printArray(arr, n);

    return 0;
}
```

---

### **Time Complexity** ⏳

- **Best Case:** O(n) (Already sorted)
- **Average Case:** O(n²)
- **Worst Case:** O(n²)

### **Space Complexity** 🗃️

- O(1) (Sorts in-place, no extra memory needed)

---

### **Where is it useful?**

✅ **Good for small arrays**  
✅ **Efficient when the array is already nearly sorted**  
🚫 **Not efficient for large arrays**

Would you like an optimized version? 🚀