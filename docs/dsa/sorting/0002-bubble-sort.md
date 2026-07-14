
# Bubble Sort

> "The simplest sorting algorithm is rarely used in production, but it teaches one of the most important engineering lessons: optimization through early termination."

---

# Problem Information

| Field | Value |
|-------|-------|
| Platform | TakeUForward (TUF+) |
| Difficulty | Easy |
| Topic | Sorting |
| Pattern | Bubble Sort |
| Status | Solved |
| Language | Java |
| Date Solved | 2026-07-14 |

---

# Problem Statement

Given an integer array `nums`, sort the array in **non-decreasing order** using the Bubble Sort algorithm and return the sorted array.

---

# Clarifying Questions

Before solving, I would ask:

1. Should the sorting be performed in-place?
2. Can duplicate elements exist?
3. Are negative numbers allowed?
4. Is stability required?
5. What is the maximum size of the array?

---

# Initial Thought Process

Bubble Sort repeatedly compares adjacent elements.

If the current element is greater than the next element,

swap them.

After every iteration,

the largest unsorted element reaches its correct position.

---

# Approach

For every pass:

```
Compare

↓

Swap if needed

↓

Largest element moves to the end
```

An optimization is to stop early if no swaps occur during a complete pass.

---

# Java Solution

```java
class Solution {

    private void swap(int[] nums, int left, int right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
    }

    public int[] bubbleSort(int[] nums) {

        int n = nums.length;

        for (int i = 0; i < n; i++) {

            boolean swapped = false;

            for (int j = 0; j < n - i - 1; j++) {

                if (nums[j] > nums[j + 1]) {

                    swap(nums, j, j + 1);
                    swapped = true;

                }

            }

            if (!swapped)
                break;

        }

        return nums;
    }
}
```

---

# Dry Run

Input

```
5 4 3 2 1
```

Pass 1

```
4 3 2 1 5
```

Pass 2

```
3 2 1 4 5
```

Pass 3

```
2 1 3 4 5
```

Pass 4

```
1 2 3 4 5
```

---

# Complexity Analysis

| Case | Time |
|------|------|
| Best | O(n) |
| Average | O(n²) |
| Worst | O(n²) |

Space

```
O(1)
```

---

# Pattern Recognition

Pattern

- Adjacent Swapping

Recognition Keywords

- Sort
- Adjacent comparison
- Stable sorting
- Multiple passes

---

# Common Mistakes

- Incorrect loop boundary.
- Forgetting the optimization (`swapped` flag).
- Swapping unnecessarily after the array is already sorted.

---

# Interview Discussion

### Why is Bubble Sort rarely used?

Although simple,

its worst-case complexity is **O(n²)**,

making it inefficient for large datasets.

Algorithms like Merge Sort and Quick Sort are preferred in production.

---

# Key Learnings

- Bubble Sort demonstrates iterative improvement.
- Early termination significantly improves the best-case performance.
- Extracting swap logic into a helper method improves readability.

---

# Reflection

Initially, the algorithm was straightforward.

I also implemented the optimized version using a `swapped` flag, allowing the algorithm to stop once the array became sorted.

This improves the best-case complexity from O(n²) to O(n).