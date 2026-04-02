

Imagine you have a big **pile of messy Lego pieces**, and you want to **sort them by size**. You can’t do it all at once, so you **divide the pile into smaller and smaller groups**, sort each small group, and then **merge them back together** in the correct order.

Here’s how it works:

1. **Split the pile in half** until each group has **just one piece**.
2. **Compare and merge** two groups at a time, keeping them sorted.
3. Keep merging until all pieces are **back together in order**!

This is **Merge Sort**—it **divides** and then **conquers** by sorting smaller parts first.

---

### **Merge Sort Algorithm** 📝

1. **Divide** the array into two halves.
2. **Recursively** sort each half.
3. **Merge** the sorted halves by comparing elements one by one.

---

### **Merge Sort Code in C** 💻

```c
#include <stdio.h>

// Function to merge two halves
void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    int leftArr[n1], rightArr[n2];

    // Copy data to temp arrays
    for (int i = 0; i < n1; i++)
        leftArr[i] = arr[left + i];
    for (int i = 0; i < n2; i++)
        rightArr[i] = arr[mid + 1 + i];

    // Merge the temp arrays back into arr[]
    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (leftArr[i] <= rightArr[j]) {
            arr[k] = leftArr[i];
            i++;
        } else {
            arr[k] = rightArr[j];
            j++;
        }
        k++;
    }

    // Copy remaining elements of leftArr[]
    while (i < n1) {
        arr[k] = leftArr[i];
        i++;
        k++;
    }

    // Copy remaining elements of rightArr[]
    while (j < n2) {
        arr[k] = rightArr[j];
        j++;
        k++;
    }
}

// Merge Sort function
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        // Recursively sort first and second halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
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

    mergeSort(arr, 0, n - 1);

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

- O(n) (Uses extra space for merging)

---

### **Where is it useful?**

✅ **Very efficient for large datasets**  
✅ **Guaranteed O(n log n) performance**  
✅ **Stable sorting (keeps order of equal elements)**  
🚫 **Uses extra memory for merging**

Would you like an optimized version or another sorting method? 🚀