# Check if the Array is Sorted I

> "The first step toward solving complex problems is mastering simple observations."

---

# Problem Information

| Field | Value |
|-------|-------|
| Platform | TakeUForward (TUF+) |
| Difficulty | Easy |
| Topic | Arrays |
| Pattern | Linear Traversal |
| Status |  Solved |
| Language | Java |
| Date Solved | 2026-07-08 |

---

# Problem Statement

Given an integer array, determine whether the array is sorted in **non-decreasing order**.

Return:

- `true` if sorted
- `false` otherwise

---

# Clarifying Questions

Before solving, I would ask:

1. Is the array sorted in ascending or descending order?
2. Are duplicate values allowed?
3. Can the array contain negative numbers?
4. Can the array be empty?
5. Can it contain only one element?

---

# Initial Thought Process

My first intuition was straightforward.

If every element is **less than or equal to the next element**, then the array is sorted.

So I only need to compare:

```
arr[i]
↓

arr[i + 1]
```

The moment I find

```
arr[i] > arr[i + 1]
```

the array is not sorted.

No extra space is required.

---

# Approach

Traverse the array once.

Compare every adjacent pair.

If any previous element is greater than the next one,

return `false`.

If the loop completes successfully,

return `true`.

---

# Java Solution

```java
class Solution {

    boolean arraySortedOrNot(int[] arr, int n) {

        for (int i = 0, j = 1; j < n; i++, j++) {

            if (arr[i] > arr[j]) {
                return false;
            }

        }

        return true;
    }

}
```

---

# Complexity Analysis

| Metric | Complexity |
|---------|------------|
| Time | O(n) |
| Space | O(1) |

Reason:

Each element is visited only once.

---

# Pattern Recognition

## Pattern

- Linear Traversal

### Recognition Keywords

- Check every element
- Verify ordering
- Adjacent comparison
- Validation problem

---

# Edge Cases

| Input | Output |
|--------|---------|
| [] | true |
| [5] | true |
| [1,2,3] | true |
| [1,1,2] | true |
| [5,4] | false |

---

# Common Mistakes

- Forgetting duplicates are valid.
- Comparing incorrect indices.
- Iterating beyond array bounds.

---

# Interview Discussion

### Follow-up Questions

Can you solve it recursively?

Can you check descending order?

Can you check if an array is strictly increasing?

---

# Key Learnings

- Many array validation problems require only one pass.
- Returning immediately when a condition fails improves readability.
- Always think about edge cases before coding.

---

# Revision Notes

- Compare adjacent elements.

- Stop immediately when the order breaks.

Pattern:

Linear Scan

---

# Related Problems

- Check if Array is Sorted II
- Monotonic Array
- Remove Duplicates from Sorted Array

---

# Reflection

## Confidence

⭐⭐⭐⭐⭐☆☆☆☆☆ (5/10)

## What I Learned

Simple observation problems often don't require complex algorithms.

## What I Would Improve

I can simplify the loop by using only one variable (`i`) instead of both `i` and `j`.

Example:

```java
for (int i = 1; i < n; i++) {
    if (arr[i - 1] > arr[i]) {
        return false;
    }
}
```

This version is more common in interviews.