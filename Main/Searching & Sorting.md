
# Searching
1. [[Linear Search]]
2. [[Binary Search]]

# Sorting
1. [[Bubble Sort]]
2. [[Insertion Sort]]
3. [[Selection Sort]]
4. [[Quick Sort]]
5. [[Merge Sort]]
6. [[Heap Sort]]
7. [[Radix Sort]]




### **Comparison-Based Sorting Algorithms**

1. **Bubble Sort** 🫧
    
    - Repeatedly swaps adjacent elements if they are in the wrong order.
    - **Best:** O(n), **Avg/Worst:** O(n²), **Space:** O(1), **Stable:** ✅
2. **Selection Sort** 🔎
    
    - Repeatedly finds the smallest element and swaps it with the first unsorted element.
    - **Best/Avg/Worst:** O(n²), **Space:** O(1), **Stable:** ❌
3. **Insertion Sort** 📌
    
    - Builds the sorted array one element at a time by inserting it into the correct position.
    - **Best:** O(n), **Avg/Worst:** O(n²), **Space:** O(1), **Stable:** ✅
4. **Merge Sort** 🔀
    
    - Recursively splits the array into halves, sorts them, and merges the sorted halves.
    - **Best/Avg/Worst:** O(n log n), **Space:** O(n), **Stable:** ✅
5. **Quick Sort** ⚡
    
    - Selects a pivot, partitions the array around it, and recursively sorts the subarrays.
    - **Best/Avg:** O(n log n), **Worst:** O(n²) (if poorly chosen pivot), **Space:** O(log n) (avg), **Stable:** ❌
6. **Heap Sort** ⛰️
    
    - Converts the array into a heap and repeatedly extracts the maximum element.
    - **Best/Avg/Worst:** O(n log n), **Space:** O(1), **Stable:** ❌
7. **Shell Sort** 🐚
    
    - A variation of insertion sort that compares elements at a certain gap and gradually reduces the gap.
    - **Best:** O(n log n), **Avg:** O(n log² n), **Worst:** O(n²), **Space:** O(1), **Stable:** ❌

### **Non-Comparison Sorting Algorithms** (Work on specific conditions)

1. **Counting Sort** 🔢
    
    - Counts occurrences of elements and reconstructs the sorted array. Works only for integers in a limited range.
    - **Best/Avg/Worst:** O(n + k), **Space:** O(k), **Stable:** ✅
9. **Radix Sort** 🏁
    
    - Sorts numbers digit by digit using Counting Sort as a subroutine. Works well for numbers and strings.
    - **Best/Avg/Worst:** O(nk), **Space:** O(n + k), **Stable:** ✅
10. **Bucket Sort** 🪣
    
    - Distributes elements into buckets, sorts them individually, and then combines them.
    - **Best/Avg:** O(n + k), **Worst:** O(n²), **Space:** O(n + k), **Stable:** ✅

Would you like any specific explanation or implementation examples? 🚀