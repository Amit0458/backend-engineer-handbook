# Sum of Highest and Lowest Frequency

> "Frequency counting is a pattern. Once mastered, many array problems become simple."

---

# Problem Information

| Field | Value |
|-------|-------|
| Platform | TakeUForward (TUF+) |
| Difficulty | Easy |
| Topic | Arrays, HashMap |
| Pattern | Frequency Counting |
| Status | Solved |
| Language | Java |
| Date Solved | 2026-07-14 |

---

# Problem Statement

Given an integer array,

find the highest frequency and the lowest frequency of any element.

Return the sum of both frequencies.

---

# Clarifying Questions

1. Are duplicate elements allowed?
2. Can the array contain only one unique element?
3. Should frequencies be calculated for distinct values only?
4. Can numbers be negative?

---

# Initial Thought Process

The problem naturally divides into two phases:

1. Count frequencies.
2. Find the maximum and minimum frequencies.

A HashMap is the ideal data structure for counting occurrences efficiently.

---

# Approach

Step 1

```
Element

↓

Frequency
```

using a HashMap.

Step 2

Traverse all frequency values.

Update

- Maximum Frequency
- Minimum Frequency

Return

```
maxFrequency + minFrequency
```

---

# Java Solution

```java
class Solution {

    public int sumHighestAndLowestFrequency(int[] nums) {

        Map<Integer, Integer> numsFreq = new HashMap<>();

        int maxFreq = 0;
        int minFreq = nums.length;

        for (int num : nums) {
            numsFreq.put(num, numsFreq.getOrDefault(num, 0) + 1);
        }

        for (int freq : numsFreq.values()) {
            minFreq = Math.min(minFreq, freq);
            maxFreq = Math.max(maxFreq, freq);
        }

        return minFreq + maxFreq;
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

Pattern

- Frequency Counting

Recognition Keywords

- Count occurrences
- Maximum frequency
- Minimum frequency
- Duplicates

---

# Common Mistakes

- Initializing `minFreq` incorrectly.
- Forgetting to build the frequency map first.
- Mixing element values with frequency values.

---

# Related Problems

- Highest Occurring Element
- Second Highest Frequency
- Top K Frequent Elements
- Majority Element

---

# Key Learnings

Whenever a problem asks about occurrences,

think of

```
HashMap<Element, Frequency>
```

before considering more complex data structures.

---

# Reflection

This problem reinforced the frequency-counting pattern.

Once the HashMap was built,

finding both the maximum and minimum frequencies became a simple traversal over the map values.