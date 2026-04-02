Below is a detailed, step‐by‐step simulation of Quick Sort on the array `{25, 57, 48, 37, 12, 92, 86, 33}`
 
using your code. We’ll show each partition call (using Lomuto’s scheme) with its corresponding table. In these tables, note that even a “self‑swap” (swapping an element with itself) is executed by the code but leaves the array unchanged.

---

## Partition 1: partition(arr, 0, 7)

- **Subarray:** [25, 57, 48, 37, 12, 92, 86, 33]
- **Pivot:** 33   (chosen as arr[7])
- **Initial i:** low – 1 = 0 – 1 = –1

|**Step**|**j**|**arr[j]**|**Condition (arr[j] < 33?)**|**i before**|**Action**|**i after**|**Array State**|
|---|---|---|---|---|---|---|---|
|Iteration 1|0|25|25 < 33 → True|–1|Increment i to 0; swap arr[0] with arr[0] (self‑swap)|0|[25, 57, 48, 37, 12, 92, 86, 33]|
|Iteration 2|1|57|57 < 33 → False|0|No action|0|[25, 57, 48, 37, 12, 92, 86, 33]|
|Iteration 3|2|48|48 < 33 → False|0|No action|0|[25, 57, 48, 37, 12, 92, 86, 33]|
|Iteration 4|3|37|37 < 33 → False|0|No action|0|[25, 57, 48, 37, 12, 92, 86, 33]|
|Iteration 5|4|12|12 < 33 → True|0|Increment i to 1; swap arr[1] with arr[4] (swapping 57 and 12)|1|[25, 12, 48, 37, 57, 92, 86, 33]|
|Iteration 6|5|92|92 < 33 → False|1|No action|1|[25, 12, 48, 37, 57, 92, 86, 33]|
|Iteration 7|6|86|86 < 33 → False|1|No action|1|[25, 12, 48, 37, 57, 92, 86, 33]|
|**Final Swap**|–|Pivot (33)|–|i = 1|Swap pivot with arr[i+1]: swap arr[2] (48) with arr[7] (33)|–|[25, 12, 33, 37, 57, 92, 86, 48]|

- **Pivot Index Returned:** 2
- **Array After Partition 1:** [25, 12, 33, 37, 57, 92, 86, 48]

---

## Partition 2: partition(arr, 0, 1)

This call sorts the left subarray of Partition 1.

- **Subarray:** [25, 12]  (indices 0 to 1)
- **Pivot:** 12   (arr[1])
- **Initial i:** 0 – 1 = –1

|**Step**|**j**|**arr[j]**|**Condition (arr[j] < 12?)**|**i before**|**Action**|**i after**|**Array State**|
|---|---|---|---|---|---|---|---|
|Iteration 1|0|25|25 < 12 → False|–1|No action|–1|[25, 12, 33, 37, 57, 92, 86, 48]|
|**Final Swap**|–|Pivot (12)|–|i = –1|Swap arr[i+1]=arr[0] with pivot arr[1] (swap 25 and 12)|–|[12, 25, 33, 37, 57, 92, 86, 48]|

- **Pivot Index Returned:** 0
- **Array After Partition 2:** [12, 25, 33, 37, 57, 92, 86, 48]

---

## Partition 3: partition(arr, 3, 7)

This call sorts the right subarray (indices 3 to 7) from Partition 1.

- **Subarray:** [37, 57, 92, 86, 48]  (indices 3 to 7)
- **Pivot:** 48   (arr[7])
- **Initial i:** low – 1 = 3 – 1 = 2

|**Step**|**j**|**arr[j]**|**Condition (arr[j] < 48?)**|**i before**|**Action**|**i after**|**Array State**|
|---|---|---|---|---|---|---|---|
|Iteration 1|3|37|37 < 48 → True|2|Increment i to 3; swap arr[3] with arr[3] (self‑swap)|3|[12, 25, 33, 37, 57, 92, 86, 48]|
|Iteration 2|4|57|57 < 48 → False|3|No action|3|[12, 25, 33, 37, 57, 92, 86, 48]|
|Iteration 3|5|92|92 < 48 → False|3|No action|3|[12, 25, 33, 37, 57, 92, 86, 48]|
|Iteration 4|6|86|86 < 48 → False|3|No action|3|[12, 25, 33, 37, 57, 92, 86, 48]|
|**Final Swap**|–|Pivot (48)|–|i = 3|Swap arr[i+1]=arr[4] with pivot arr[7] (swap 57 and 48)|–|[12, 25, 33, 37, 48, 92, 86, 57]|

- **Pivot Index Returned:** 4
- **Array After Partition 3:** [12, 25, 33, 37, 48, 92, 86, 57]

---

## Partition 4: partition(arr, 5, 7)

This call sorts the right subarray of Partition 3.

- **Subarray:** [92, 86, 57]  (indices 5 to 7)
- **Pivot:** 57   (arr[7])
- **Initial i:** 5 – 1 = 4

|**Step**|**j**|**arr[j]**|**Condition (arr[j] < 57?)**|**i before**|**Action**|**i after**|**Array State**|
|---|---|---|---|---|---|---|---|
|Iteration 1|5|92|92 < 57 → False|4|No action|4|[12, 25, 33, 37, 48, 92, 86, 57]|
|Iteration 2|6|86|86 < 57 → False|4|No action|4|[12, 25, 33, 37, 48, 92, 86, 57]|
|**Final Swap**|–|Pivot (57)|–|i = 4|Swap arr[i+1]=arr[5] with pivot arr[7] (swap 92 and 57)|–|[12, 25, 33, 37, 48, 57, 86, 92]|

- **Pivot Index Returned:** 5
- **Array After Partition 4:** [12, 25, 33, 37, 48, 57, 86, 92]

---

## Partition 5: partition(arr, 6, 7)

This final partition call is on the subarray [86, 92] (indices 6 to 7).

- **Subarray:** [86, 92]
- **Pivot:** 92   (arr[7])
- **Initial i:** 6 – 1 = 5

|**Step**|**j**|**arr[j]**|**Condition (arr[j] < 92?)**|**i before**|**Action**|**i after**|**Array State**|
|---|---|---|---|---|---|---|---|
|Iteration 1|6|86|86 < 92 → True|5|Increment i to 6; swap arr[6] with arr[6] (self‑swap)|6|[12, 25, 33, 37, 48, 57, 86, 92]|
|**Final Swap**|–|Pivot (92)|–|i = 6|Swap arr[i+1]=arr[7] with pivot arr[7] (self‑swap)|–|[12, 25, 33, 37, 48, 57, 86, 92]|

- **Pivot Index Returned:** 7

---

## Final Sorted Array

After all recursive calls complete, the fully sorted array is:

  **[12, 25, 33, 37, 48, 57, 86, 92]**

---

### Summary

1. **First Partition (0 to 7):**  
    Pivot 33 is placed at index 2, with the left part [25, 12] and right part [37, 57, 92, 86, 48].
    
2. **Second Partition (0 to 1):**  
    Sorting [25, 12] results in [12, 25].
    
3. **Third Partition (3 to 7):**  
    Sorting [37, 57, 92, 86, 48] with pivot 48 places 48 at index 4.
    
4. **Fourth Partition (5 to 7):**  
    Sorting [92, 86, 57] with pivot 57 places 57 at index 5.
    
5. **Fifth Partition (6 to 7):**  
    Sorting [86, 92] with pivot 92 finalizes that part.
    

Each step follows the provided code exactly, including self‑swaps that don’t change the array but are executed in the algorithm. This complete breakdown should help you understand how Quick Sort operates on your array.