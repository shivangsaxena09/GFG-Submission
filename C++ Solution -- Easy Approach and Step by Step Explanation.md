## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-infinite-string1049/1)

### Problem Description

**Task:** Given a string s and an integer pos, an infinite string is constructed by repeatedly applying the following operation. In the i-th step, append i consecutive $ characters, followed by the reverse of the current string, to the current string.Formally, if the current string is s, update it as:s = s + ('$' repeated i times) + reverse(s)The initial string is the given s, and the process continues indefinitely. Find and return the character at the pos(1-based indexing) in the resulting infinite string.Examples:Input: s = "12345", pos = 3

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** In "12345...", the character at pos 3 is 3.

##### Example 2

- **Input:**
```text
s = "12345", pos = 10
```
- **Output:**
```text
2
```
- **Explanation:** In "12345$54321...", the character at pos 10 is 2.

##### Example 3

- **Input:**
```text
s = "abc", pos = 7
```
- **Output:**
```text
a
```
- **Explanation:** In "abc$cba...", the character at pos 7 is a.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log (pos))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Java)

- **Submitted:** 2026-11-23 22:38:45
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    public char posInfinite(String s, int pos) {
        long target = pos;
        long baseLen = s.length();

        if (target <= baseLen) {
            return s.charAt((int) target - 1);
        }

        long curLen = baseLen;
        int step = 1;
        java.util.ArrayList<Long> prevLengths = new java.util.ArrayList<>();
        java.util.ArrayList<Integer> steps = new java.util.ArrayList<>();

        while (curLen < target) {
            prevLengths.add(curLen);
            steps.add(step);
            curLen = 2 * curLen + step;
            step++;
        }

        for (int idx = prevLengths.size() - 1; idx >= 0; idx--) {
            long prevLen = prevLengths.get(idx);
            int curStep = steps.get(idx);

            if (target <= prevLen) {
                curLen = prevLen;
            } else if (target <= prevLen + curStep) {
                return '$';
            } else {
                target = curLen - target + 1;
                curLen = prevLen;
            }
        }

        return s.charAt((int) target - 1);
    }
}
```

#### Solution 2 (Java)

- **Submitted:** 2026-11-23 22:38:31
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
    public char posInfinite(String s, int pos) {
        long target = pos;
        long baseLen = s.length();

        if (target <= baseLen) {
            return s.charAt((int) target - 1);
        }

        long curLen = baseLen;
        int step = 1;
        java.util.ArrayList<Long> prevLengths = new java.util.ArrayList<>();
        java.util.ArrayList<Integer> steps = new java.util.ArrayList<>();

        while (curLen < target) {
            prevLengths.add(curLen);
            steps.add(step);
            curLen = 2 * curLen + step;
            step++;
        }

        for (int idx = prevLengths.size() - 1; idx >= 0; idx--) {
            long prevLen = prevLengths.get(idx);
            int curStep = steps.get(idx);

            if (target <= prevLen) {
                curLen = prevLen;
            } else if (target <= prevLen + curStep) {
                return '$';
            } else {
                target = curLen - target + 1;
                curLen = prevLen;
            }
        }

        return s.charAt((int) target - 1);
    }
}
```

*Generated on: 23/11/2026, 22:39:02*