# Problem: Merge One Sorted Array Into Another (Constant Space)

---

## Problem Understanding

You have:

- **First array**:
  - Size = `n`
  - Sorted

- **Second array**:
  - Size = `2n`
  - First `n` elements are sorted positive numbers
  - Last `n` elements are zero placeholders

---

## 🎯 Goal

- Merge `first` into `second` **in-place** (inside `second` itself).
- Result should be a **sorted array of 2n positive numbers**.
- Important: **No extra arrays allowed** — must use **O(1) extra memory** (constant space).

---

## Code for "Merge One Sorted Array Into Another"

### Python Code

```python
def merge_sorted_arrays(first, second):
    n = len(first)
    i = n - 1            # Pointer for last element of first array
    j = n - 1            # Pointer for last non-zero element of second array
    k = 2 * n - 1        # Pointer for end of second array

    # Merge from back to front
    while i >= 0 and j >= 0:
        if first[i] > second[j]:
            second[k] = first[i]
            i -= 1
        else:
            second[k] = second[j]
            j -= 1
        k -= 1

    # If any elements left in first array
    while i >= 0:
        second[k] = first[i]
        i -= 1
        k -= 1

    return second
```
### Example Walkthrough
Input

first = [1, 3, 5]
second = [2, 4, 6, 0, 0, 0]
### Step-by-Step with Pointers

Step	i	j	k	Compare	Action	second (after update)
1	2	2	5	5 vs 6	second[5] = 6, j--	[2, 4, 6, 0, 0, 6]
2	2	1	4	5 vs 4	second[4] = 5, i--	[2, 4, 6, 0, 5, 6]
3	1	1	3	3 vs 4	second[3] = 4, j--	[2, 4, 6, 4, 5, 6]
4	1	0	2	3 vs 2	second[2] = 3, i--	[2, 4, 3, 4, 5, 6]
5	0	0	1	1 vs 2	second[1] = 2, j--	[2, 2, 3, 4, 5, 6]
6	0	-1	0	No j left	second[0] = 1 (from first), i--	[1, 2, 3, 4, 5, 6]
### Final Output

[1, 2, 3, 4, 5, 6]
### Both arrays merged properly into second.

### All done in-place (no extra array created).

### Key Insights (Simple Language)

Pointer	Meaning
i	Last number in first array
j	Last non-zero number in second array
k	Last available empty spot in second array
Start filling from the end because:

It prevents overwriting useful values.

It avoids needing extra memory.

### Why Merge from Back?
If we start merging from the beginning:

We risk overwriting elements that have not been compared yet.

Merging from back ensures we safely fill empty spaces first.

### Time and Space Complexity

Metric	Value
Time Complexity	O(n)
Space Complexity	O(1) (in-place)
