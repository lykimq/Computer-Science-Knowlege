# Binary Search

Binary search is a **divide-and-conquer** algorithm applied to a sorted array by repeatedly cutting the search range in half.

At the start, the search space is the entire array. The target value is compared with the middle element. If they are not equal, the half that cannot contain the target is discarded. The process continues on the remaining half: take the middle element, compare it with the target, and repeat until the target is found or no elements remain.

If the search ends with an empty search space, the target does not exist in the array.

The time complexity is **O(log n)** because after each step, the search space is reduced by half.

![Binary Search: The Power of Divide and Conquer](pics/Binary_Search_Algorithm_Explained.png)

The illustration above highlights:

- **Sorted array**: The algorithm works correctly only when the input data is sorted.
- **Compare and split**: Compare the target with the middle element, then discard the irrelevant half.
- **Stopping condition**: The search ends when the target is found or no elements remain to check.
- **Efficiency**: The search space shrinks by 50% after each step.

## Pseudocode

Binary search can be written in two ways: **iterative** and **recursive**.

### Iterative Approach

```
FUNCTION binarySearch(arr, target):
    left  = 0                      // first index
    right = length(arr) - 1        // last index

    WHILE left <= right:
        mid = left + floor((right - left) / 2)

        IF arr[mid] == target:
            RETURN mid             // target found

        ELSE IF arr[mid] < target:
            left = mid + 1         // discard left half (including mid)

        ELSE:
            right = mid - 1        // discard right half (including mid)

    RETURN -1                      // not found
```

### Recursive Approach

Initial call:

```
RETURN binarySearch(arr, target, 0, length(arr) - 1)
```

```
FUNCTION binarySearch(arr, target, left, right):
    IF left > right:
        RETURN -1                  // not found

    mid = left + floor((right - left) / 2)

    IF arr[mid] == target:
        RETURN mid

    ELSE IF arr[mid] < target:
        RETURN binarySearch(arr, target, mid + 1, right)   // search in right half

    ELSE:
        RETURN binarySearch(arr, target, left, mid - 1)    // search in left half
```

## Notes

- The array must be **sorted** before applying binary search.
- Use `left + (right - left) / 2` instead of `(left + right) / 2` to avoid integer overflow when `left` and `right` are very large.
- Time complexity: **O(log n)**.
- Space complexity: **O(1)** for the iterative approach, **O(log n)** for the recursive approach (due to the call stack).
