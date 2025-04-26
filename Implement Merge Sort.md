# Problem: Implement Merge Sort

## Problem Statement

Given a list of numbers, sort it using the **Merge Sort** algorithm.

---

## Example

**Input:**

```json
{
  "arr": [5, 8, 3, 9, 4, 1, 7]
}
```
Output:

```json
[1, 3, 4, 5, 7, 8, 9]
```

Solution
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(left, right):
    merged = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            merged.append(left[i])
            i += 1
        else:
            merged.append(right[j])
            j += 1
    merged.extend(left[i:])
    merged.extend(right[j:])

    return merged
```
### Explanation
Step 1: If the array has one or no elements, it is already sorted.

Step 2: Otherwise:

Divide the array into two halves: left and right.

Recursively apply merge_sort to both halves.

## Step 3: Merge the two sorted halves using the merge function.

How merge Works
Compare the first elements of left and right.

Append the smaller element to the merged list.

Continue comparing and appending until one list is exhausted.

Append any remaining elements from left or right to merged.

### Time and Space Complexity

Aspect	Complexity
Time Complexity	O(n log n)
Space Complexity	O(n)
Merge Sort is efficient for large datasets.

