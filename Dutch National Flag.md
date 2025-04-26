# Problem: Dutch National Flag

## Problem Statement

Given some balls of three colors arranged in a line, rearrange them such that:
- All the red balls (`'R'`) go first,
- Then green balls (`'G'`),
- Then blue balls (`'B'`).

Do rearrange the balls **in place**.  
A solution that simply counts colors and overwrites the array is **not acceptable** — the rearrangement must be **in-place**.

This is an important problem in search algorithm theory, proposed by Dutch computer scientist **Edsger Dijkstra**.  
(The Dutch national flag has three colors, albeit different ones.)

---

## Example

**Input:**

```json
{
  "balls": ["G", "B", "G", "G", "R", "B", "R", "G"]
}
```

### Output:

``` json
["R", "R", "G", "G", "G", "G", "B", "B"]
```
There are a total of:

2 red balls,

4 green balls,

2 blue balls.


In this order, they appear correctly in the output.

### Solution
```python
def dutch_national_flag_sort(balls):
    """
    Sort balls in-place: Reds first, then Greens, then Blues.
    :param balls: List of characters ['R', 'G', 'B']
    :return: Sorted list in-place
    """
    low = 0                # Start of the array (for Reds)
    mid = 0                # Current index
    high = len(balls) - 1  # End of the array (for Blues)

    while mid <= high:
        if balls[mid] == 'R':
            # Swap with low and move both forward
            balls[low], balls[mid] = balls[mid], balls[low]
            low += 1
            mid += 1
        elif balls[mid] == 'G':
            # Correct position, just move forward
            mid += 1
        else:  # balls[mid] == 'B'
            # Swap with high and move high backward
            balls[mid], balls[high] = balls[high], balls[mid]
            high -= 1

    return balls
```
### Time & Space Complexity

Metric	Value
Time Complexity	O(n)
Space Complexity	O(1)
Step-by-Step Execution Table

Step	low	mid	high	balls[mid]	Action	Updated balls
1	0	0	7	G	It's green → just move mid	["G", "B", "G", "G", "R", "B", "R", "G"]
2	0	1	7	B	Swap with high (G), high--	["G", "G", "G", "G", "R", "B", "R", "B"]
3	0	1	6	G	It's green → just move mid	["G", "G", "G", "G", "R", "B", "R", "B"]
4	0	2	6	G	It's green → just move mid	["G", "G", "G", "G", "R", "B", "R", "B"]
5	0	3	6	G	It's green → just move mid	["G", "G", "G", "G", "R", "B", "R", "B"]
6	0	4	6	R	Swap with low (G), low++, mid++	["R", "G", "G", "G", "G", "B", "R", "B"]
7	1	5	6	B	Swap with high (R), high--	["R", "G", "G", "G", "G", "R", "B", "B"]
8	1	5	5	R	Swap with low (G), low++, mid++	["R", "R", "G", "G", "G", "G", "B", "B"]
Notes
The algorithm rearranges the balls in-place with constant space.

It ensures all 'R' are before 'G', which are before 'B'.

Inspired by real-world applications like 3-way partitioning in quicksort.
