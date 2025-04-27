## What is "Big O" (O-notation)?
"Big O" tells us how fast or slow a program grows as input size increases.

It ignores small things (like 2 seconds vs 3 seconds) and focuses on the trend.

It only cares about the biggest factor when n (input size) becomes large.

📚 ### Common Time Complexities

Name	O-notation	Meaning
Constant Time	O(1)	No matter the input size, it takes the same time.
Linear Time	O(n)	Time grows directly with input size.
Logarithmic Time	O(log n)	Time grows slowly even if input size is big.
Linearithmic Time	O(n log n)	Grows faster than O(n), but slower than O(n²).
Quadratic Time	O(n²)	Time grows with square of input size.
Cubic Time	O(n³)	Time grows with cube of input size.
Exponential Time	O(2ⁿ)	Time doubles with each extra input.
🛠️ 1. O(1) - Constant Time
Meaning: Always takes the same time, no matter how big the input is.

Example:

```python

def get_first_element(arr):
    return arr[0]
```
Whether arr has 10 elements or 1 million, picking the first element is just 1 step.

✅ Time = O(1)

🛠️ 2. O(n) - Linear Time
Meaning: Time grows directly with input size.

Example:

```python

def print_all_elements(arr):
    for element in arr:
        print(element)
```
If arr has 10 elements ➔ 10 prints.

If arr has 1000 elements ➔ 1000 prints.

✅ Time = O(n)

🛠️ 3. O(n²) - Quadratic Time
Meaning: Time grows as the square of input size. (n × n)

Example:

python
Copy
Edit
def print_pairs(arr):
    for i in arr:
        for j in arr:
            print(i, j)
If arr has 5 elements ➔ 5 × 5 = 25 pairs.

If arr has 100 elements ➔ 100 × 100 = 10,000 pairs!

✅ Time = O(n²)

🧠 Rule: Nested loops = Often O(n²)

🛠️ 4. O(log n) - Logarithmic Time
Meaning: Time grows very slowly, even if input grows fast.

Example:

python
Copy
Edit
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
You divide the list by half each time.

Searching in 1,000,000 elements = only about 20 steps!

✅ Time = O(log n)

📚 Memory Tip:
"Every step cuts work in half = O(log n)"

🛠️ 5. O(n log n) - Linearithmic Time
Meaning: A little slower than O(n), but much faster than O(n²).

Example:

Merge Sort or Heap Sort algorithms.

Real-world example: Sorting a huge list.

python
Copy
Edit
# Merge sort (concept)
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)
✅ Time = O(n log n)

Splitting is log n.

Merging all items is n.

Together ➔ O(n log n).

🎨 Quick Visual Feeling (How Fast They Grow)

n = 10	n = 100	n = 1000
O(1)	1	1
O(log n)	3	6
O(n)	10	100
O(n log n)	30	600
O(n²)	100	10,000
O(2ⁿ)	1024	(impossible huge)
🧠 Easy Memory Trick 🎯

O(1)	Instant
O(log n)	Cuts in half again and again
O(n)	1 step for 1 item
O(n log n)	1 step + half splits
O(n²)	Compare everything to everything
🔥 Summary Table

Name	Common Example	Time Growth
O(1)	Accessing first element	🚀 Very Fast
O(n)	For loop through list	🏃‍♂️ Grows with input
O(log n)	Binary search	🐢 Very Slow Growth
O(n log n)	Merge Sort	⚡ Medium
O(n²)	Nested loops (compare all)	🐘 Slow
