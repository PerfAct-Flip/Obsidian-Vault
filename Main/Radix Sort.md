
Imagine you have a **box of numbers written on cards**, and you want to **sort them** from smallest to largest. But instead of comparing them directly, you **sort them digit by digit** from the **rightmost** (ones place) to the **leftmost** (highest place value).

Here’s how it works:

1. First, **sort all the numbers based on the last digit** (ones place).
2. Then, **sort again based on the second-last digit** (tens place).
3. Repeat this process for **hundreds, thousands, etc.**, until all digits are sorted.
4. The numbers will now be in **perfect order**!

**Radix Sort is special** because it doesn’t compare numbers directly. Instead, it uses **digit-by-digit sorting**, usually with **Counting Sort** as a helper.

---

### **Radix Sort Algorithm** 📝

1. Find the **largest number** (to know the number of digits).
2. Start sorting from the **least significant digit (LSD)** (ones place).
3. Use **Counting Sort** to group numbers by their current digit.
4. Move to the **next digit (tens, hundreds, etc.)** and repeat until all digits are sorted.

---

### **Radix Sort Code in C** 💻

```c
#include <stdio.h>

// Function to get the maximum value in an array
int getMax(int arr[], int n) {
    int max = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > max)
            max = arr[i];
    return max;
}

// Function to perform Counting Sort for a specific digit place
void countingSort(int arr[], int n, int place) {
    int output[n];  // Output array
    int count[10] = {0};  // Count array (digits 0-9)

    // Count occurrences of each digit at the current place
    for (int i = 0; i < n; i++)
        count[(arr[i] / place) % 10]++;

    // Convert count array to cumulative count
    for (int i = 1; i < 10; i++)
        count[i] += count[i - 1];

    // Build the output array
    for (int i = n - 1; i >= 0; i--) {
        output[count[(arr[i] / place) % 10] - 1] = arr[i];
        count[(arr[i] / place) % 10]--;
    }

    // Copy the sorted numbers back into the original array
    for (int i = 0; i < n; i++)
        arr[i] = output[i];
}

// Function to perform Radix Sort
void radixSort(int arr[], int n) {
    int max = getMax(arr, n);  // Find the maximum number

    // Sort for every digit (ones, tens, hundreds, etc.)
    for (int place = 1; max / place > 0; place *= 10)
        countingSort(arr, n, place);
}

// Function to print an array
void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {170, 45, 75, 90, 802, 24, 2, 66};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original Array: ");
    printArray(arr, n);

    radixSort(arr, n);

    printf("Sorted Array: ");
    printArray(arr, n);

    return 0;
}
```

---

### **Time Complexity** ⏳

- **Best Case:** O(nk)
- **Average Case:** O(nk)
- **Worst Case:** O(nk)

(Where **n** is the number of elements, and **k** is the number of digits in the largest number.)

### **Space Complexity** 🗃️

- O(n + k) (Uses extra space for sorting)

---

### **Where is it useful?**

✅ **Great for sorting large numbers**  
✅ **Stable (keeps order of equal elements)**  
✅ **Faster than Quick Sort for small digit-based numbers**  
🚫 **Doesn’t work well for floating points, negatives, or non-integer data**

Would you like a step-by-step visualization? 🚀