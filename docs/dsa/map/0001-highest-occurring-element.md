# Highest Occurring Element in an Array

> "Frequency counting is one of the most fundamental patterns in DSA."

---

# Problem Information

| Field | Value |
|-------|-------|
| Platform | TakeUForward (TUF+) |
| Difficulty | Easy |
| Topic | Arrays, Hashing |
| Pattern | Frequency Counting |
| Status | Solved |
| Language | Java |
| Date Solved | 2026-07-13 |

---

# Problem Statement

Given an integer array, return the element that appears the highest number of times.

If multiple elements have the same highest frequency, return the smallest element.

---

# Clarifying Questions

Before solving, I would ask:

1. Can the array contain duplicate values?
2. What should be returned if multiple elements have the same frequency?
3. Can numbers be negative?
4. Is the array guaranteed to contain at least one element?

---

# Initial Thought Process

My first thought was to count the frequency of every element.

A HashMap is the best choice because it allows storing:

```
Element -> Frequency
```

While updating the frequency, I can simultaneously keep track of:

- Maximum frequency seen so far.
- Corresponding element.

This avoids making another pass through the map.

---

# Approach

1. Traverse the array once.
2. Store frequency using a HashMap.
3. Update the answer whenever:
   - Current frequency becomes greater than the maximum frequency.
   - Frequencies are equal but the current element is smaller.

---

# Java Solution

```java
class Solution {

    public int mostFrequentElement(int[] nums) {

        Map<Integer, Integer> numFrequency = new HashMap<>();

        int maxFreq = 0;
        int maxFreqValue = Integer.MAX_VALUE;

        for (int element : nums) {

            int freq = numFrequency.getOrDefault(element, 0) + 1;
            numFrequency.put(element, freq);

            if (freq > maxFreq ||
               (freq == maxFreq && element < maxFreqValue)) {

                maxFreq = freq;
                maxFreqValue = element;

            }
        }

        return maxFreqValue;
    }
}
```

---

# Complexity Analysis

| Metric | Complexity |
|---------|------------|
| Time | O(n) |
| Space | O(n) |

---

# Pattern Card

Pattern:

- Frequency Counting using HashMap

Recognition Keywords:

- Highest frequency
- Count occurrences
- Duplicate elements

---

# Key Learnings

- HashMap is the default choice for frequency-based problems.
- Track the answer while counting instead of making another traversal.
- Always pay attention to tie-breaking conditions.

---

# Related Problems

- Majority Element
- Top K Frequent Elements
- Sort Characters By Frequency

---

# Reflection

Initially, I recognized that frequency counting was required.

Instead of counting first and processing later, I optimized the solution by updating the answer during the same traversal.

This reduced unnecessary work and kept the solution clean.