# Selection Sort

> "Selection Sort teaches a simple but powerful idea: repeatedly select the best candidate and place it in its final position."

---

# Problem Information

| Field | Value |
|-------|-------|
| Platform | TakeUForward (TUF+) |
| Difficulty | Easy |
| Topic | Sorting |
| Pattern | Selection Sort |
| Status | Solved |
| Language | Java |
| Date Solved | 2026-07-15 |

---

# Problem Statement

Given an integer array `nums`, sort the array in **non-decreasing order** using the **Selection Sort** algorithm.

The sorting should be performed **in-place**.

---

# Clarifying Questions

Before solving, I would ask:

1. Should the array be modified in-place?
2. Are duplicate values allowed?
3. Can negative numbers exist?
4. Is the sorting required to be stable?
5. What are the input constraints?

---

# Initial Thought Process

Unlike Bubble Sort, where adjacent elements are swapped repeatedly,

Selection Sort works differently.

At every iteration,

I find the **smallest element** from the unsorted portion of the array.

Then,

I swap it with the current index.

After each iteration,

the left portion of the array becomes permanently sorted.

---

# Approach

For every index `i`:

```
Find minimum element

↓

Remember its index

↓

Swap with current position

↓

Move boundary forward
```

---

# Visualization

Initial Array

```
64 25 12 22 11
 ^
```

Find minimum

```
11
```

Swap

```
11 25 12 22 64
```

Now move to next position.

Repeat until the array is sorted.

---

# Java Solution

```java
class Solution {

    public int[] selectionSort(int[] nums) {

        int n = nums.length;

        for (int i = 0; i < n - 1; i++) {

            int minIndex = i;

            for (int j = i + 1; j < n; j++) {

                if (nums[j] < nums[minIndex]) {
                    minIndex = j;
                }

            }

            int temp = nums[minIndex];
            nums[minIndex] = nums[i];
            nums[i] = temp;

        }

        return nums;
    }
}
```

---

# Dry Run

Input

```
5 4 2 1 3
```

Pass 1

Find minimum

```
1
```

Swap

```
1 4 2 5 3
```

---

Pass 2

Find minimum

```
2
```

Swap

```
1 2 4 5 3
```

---

Pass 3

Find minimum

```
3
```

Swap

```
1 2 3 5 4
```

---

Pass 4

Find minimum

```
4
```

Swap

```
1 2 3 4 5
```

Done.

---

# Complexity Analysis

| Case | Time |
|------|------|
| Best | O(n²) |
| Average | O(n²) |
| Worst | O(n²) |

Space

```
O(1)
```

---

# Pattern Recognition

## Pattern

- Selection

---

## Recognition Keywords

- Find minimum
- Place element
- Sorting
- In-place
- Selection

---

# How did I recognize this pattern?

The problem explicitly asked for **Selection Sort**.

The key idea is:

> During each iteration, select the smallest element from the remaining unsorted part of the array and place it in its correct position.

---

# Edge Cases

| Input | Output |
|--------|---------|
| [] | [] |
| [5] | [5] |
| [2,1] | [1,2] |
| [3,3,2] | [2,3,3] |

---

# Common Mistakes

- Forgetting to reset `minIndex` for every iteration.
- Starting the inner loop from `0` instead of `i + 1`.
- Swapping inside the inner loop instead of after finding the minimum.
- Accidentally comparing indices instead of values.

---

# Interview Discussion

### Why is Selection Sort not commonly used?

Although it performs fewer swaps than Bubble Sort,

it still performs

```
O(n²)
```

comparisons regardless of whether the array is already sorted.

Therefore,

algorithms such as Merge Sort, Quick Sort, and TimSort are preferred in production systems.

---

# Bubble Sort vs Selection Sort

| Bubble Sort | Selection Sort |
|-------------|----------------|
| Swaps many times | Swaps once per pass |
| Stable | Not Stable |
| Best Case O(n) (optimized) | Best Case O(n²) |
| Adjacent swapping | Select minimum element |

---

# Key Learnings

- Selection Sort always performs the same number of comparisons.
- Only one swap is needed per iteration.
- The sorted portion of the array grows from left to right.
- Simplicity comes at the cost of efficiency.

---

# Reflection

Initially, I understood that I needed to find the minimum element in each iteration.

Once the minimum element was identified, swapping it with the current position naturally moved the sorted boundary forward.

Compared to Bubble Sort, this algorithm performs fewer swaps but does not benefit from early termination on already sorted arrays.

---

# Revision Notes

## Remember

Selection Sort

```
Find Minimum

↓

Swap Once

↓

Repeat
```

---

# Related Problems

- Bubble Sort
- Insertion Sort
- Sort Colors
- Kth Smallest Element

---

# Confidence

⭐⭐⭐⭐⭐⭐⭐☆☆☆ (7/10)

I understand the algorithm and can implement it without referring to notes.

Next goal is to compare it with Bubble Sort and Insertion Sort in terms of time complexity, stability, and practical usage.