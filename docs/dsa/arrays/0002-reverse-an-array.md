# Reverse an Array

> "The simplest solution is often the one that modifies the data in-place."

---

# Problem Information

| Field | Value |
|-------|-------|
| Platform | TakeUForward (TUF+) |
| Difficulty | Easy |
| Topic | Arrays |
| Pattern | Two Pointers |
| Status | Solved |
| Language | Java |
| Date Solved | 2026-07-08 |

---

# Problem Statement

Reverse the given array **in-place**.

No additional array should be created.

---

# Clarifying Questions

Before solving, I would ask:

1. Should the array be modified in-place?
2. Can I use extra memory?
3. Can the array contain duplicate values?
4. What is the maximum size of the array?
5. What should happen for empty arrays?

---

# Initial Thought Process

Initially I became confused because the method returns `void`.

My first idea was:

```
Create another array

↓

Store reversed elements

↓

Copy back to original array
```

Then I remembered a swapping technique I had used previously.

Instead of creating another array,

I can swap

```
First

↓

Last
```

then

```
Second

↓

Second Last
```

until both pointers meet.

This reduces the extra space to **O(1)**.

---

# Approach

Maintain two pointers.

```
Left  -> starts from index 0

Right -> starts from index n-1
```

Swap both values.

Move:

```
left++

right--
```

Continue until

```
left >= right
```

---

# Java Solution

```java
class Solution {

    public void reverse(int[] arr, int n) {

        for (int i = 0, j = n - 1; i < j; i++, j--) {

            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;

        }

    }

}
```

---

# Complexity Analysis

| Metric | Complexity |
|---------|------------|
| Time | O(n) |
| Space | O(1) |

---

# Pattern Recognition

## Pattern

- Two Pointer

---

## Recognition Keywords

- Reverse
- Swap
- In-place
- Left & Right
- Symmetry

---

# Dry Run

Input

```
1 2 3 4 5
```

Iteration 1

```
5 2 3 4 1
```

Iteration 2

```
5 4 3 2 1
```

Pointers meet.

Done.

---

# Edge Cases

| Input | Output |
|--------|---------|
| [] | [] |
| [5] | [5] |
| [1,2] | [2,1] |
| [1,2,3] | [3,2,1] |

---

# Common Mistakes

- Creating an unnecessary second array.
- Forgetting to decrement the right pointer.
- Using `i <= j`, causing an unnecessary middle-element swap.
- Forgetting that the method modifies the array directly.

---

# Interview Discussion

### Follow-up Questions

Can you reverse recursively?

Can you reverse only a subarray?

Can you reverse every K elements?

---

# Key Learnings

- Whenever a problem mentions **reverse**, immediately think of the Two Pointer pattern.
- In-place algorithms usually reduce memory usage.
- The function returning `void` often hints that the input should be modified directly.

---

# Revision Notes

Pattern:

Two Pointer

Recognition:

```
Beginning

↓

End

↓

Swap

↓

Move Towards Center
```

---

# Related Problems

- Reverse String
- Reverse Linked List
- Rotate Array

---

# Reflection

## Confidence

⭐⭐⭐⭐⭐⭐☆☆☆☆ (6/10)

## Biggest Learning

Initially, I overcomplicated the solution by thinking about creating another array.

After reflecting on previous problems, I recognized that swapping from both ends was a simpler and more efficient approach.

This reinforces an important lesson:

> Before creating extra data structures, ask yourself: **"Can this be solved in-place?"**