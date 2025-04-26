# Problem 1: Segregate Even And Odd Numbers

## Problem Statement

Given an array of numbers, rearrange them **in-place** so that even numbers appear before odd ones.

### Example

Input:
```json
{
  "numbers": [1, 2, 3, 4]
}
```
Output:

[4, 2, 3, 1]
The order within the group of even numbers does not matter; same with odd numbers. So the following are also correct outputs: [4, 2, 1, 3], [2, 4, 1, 3], [2, 4, 3, 1].

### Solutions:
```python
def segregate_evens_and_odds(numbers):

    n = len(numbers)
    j = -1
    for i in range(n):
        print(numbers[i],numbers[j])
        if numbers[i] % 2 == 0:
            j += 1
            numbers[i],numbers[j]=numbers[j],numbers[i]
            print(numbers[i],numbers[j])
    return numbers
```

### Explanation
n is the length of the array.

j keeps track of the last position where an even number was placed.

For each number in the array:

If the number is even, increment j and swap the current number with the number at index j.

This way, all even numbers are moved to the front.
