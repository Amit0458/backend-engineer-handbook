# Second Highest Occurring Element

> "Sometimes the hardest part of a problem isn't counting—it is maintaining the ordering."

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

Return the element having the second highest frequency.

If multiple elements have the same frequency, return the smallest element.

If no such element exists, return -1.

---

# Initial Thought Process

I divided the problem into three parts.

1. Count frequencies.
2. Find the second highest frequency.
3. Find the smallest element having that frequency.

To obtain the second highest frequency efficiently, I used a TreeSet.

---

# Approach

Step 1

Create

```
HashMap<Element, Frequency>
```

Step 2

Store all unique frequencies in a TreeSet.

```
1

2

5

7
```

Remove the highest frequency.

Now the last element becomes the second highest frequency.

Step 3

Traverse the HashMap and return the smallest element having that frequency.

---

# Java Solution

```java
import java.util.concurrent.atomic.AtomicInteger;

class Solution {
    public int secondMostFrequentElement(int[] nums) {

        Map<Integer, Integer> elementsFreq = new HashMap<>();
        NavigableSet<Integer> orderedUniqFreq = new TreeSet<>();

        for(int num: nums) {
            int numFreq = elementsFreq.getOrDefault(num, 0)+1;
            elementsFreq.put(num, numFreq);
        }

        for(int eFreq: elementsFreq.values())
            orderedUniqFreq.add(eFreq);

        if (orderedUniqFreq.size() <= 1)
            return -1;
        
        orderedUniqFreq.remove(orderedUniqFreq.last());
        Integer secondFreqEle = orderedUniqFreq.last();
    
        AtomicInteger minElement = new AtomicInteger(Integer.MAX_VALUE);
        
        elementsFreq.forEach((key, value) -> {
            if(value == secondFreqEle && key < minElement.get())
                minElement.set(key);
        });

        return minElement.get();
     
    }
}


```

---

# Complexity Analysis

| Metric | Complexity |
|---------|------------|
| Time | O(n log n) |
| Space | O(n) |

Reason:

TreeSet insertion requires O(log n).

---

# Pattern Card

Pattern:

Frequency Counting + Ordered Set

Recognition Keywords:

- Second maximum
- Frequency
- Ordered values

---

# Alternative Approach

Instead of TreeSet,

we can keep track of:

```
Highest Frequency

↓

Second Highest Frequency
```

while iterating over the frequency map.

That removes the TreeSet entirely.

Complexity becomes

```
O(n)
```

instead of

```
O(n log n)
```

---

# Reflection

The solution is correct.

However, after reviewing it, I realized the TreeSet can be avoided.

Maintaining the top two frequencies manually results in a simpler and faster implementation.