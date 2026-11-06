## 01. Balanced Binary Tree Counter

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/bbt-counter4914/1)

### Problem Description

**Task:** Given a height h, find the maximum number of distinct balanced binary trees of height exactly h.A binary tree is balanced if, for every node, the heights of its left and right subtrees differ by at most 1. A tree with a single node has height 1. An empty tree has height 0.Note: Since the answer can be very large, return it modulo 10⁹ + 7.Examples:Input: h = 1Output: 1Explanation: Only one tree of height 1 exists i.e. a single node.Input: h = 2

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** 3 distinct balanced trees of height 2 exist.

##### Example 2

- **Input:**
```text
h = 3
```
- **Output:**
```text
15
```
- **Explanation:** 15 distinct balanced trees of height 3 exist.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Java)

- **Submitted:** 2026-11-06 23:15:37
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    static final long MOD = 1_000_000_007L;

    public int countBT(int h) {
        if (h <= 1) return 1;
        long prev2 = 1; 
        long prev1 = 1; 
        for (int i = 2; i <= h; i++) {
            long cur = (prev1 * prev1 % MOD + 2 * prev1 % MOD * prev2 % MOD) % MOD;
            prev2 = prev1;
            prev1 = cur;
        }
        return (int) prev1;
    }
}
```

#### Solution 2 (Java)

- **Submitted:** 2026-11-06 22:36:51
- **Status:** Correct
- **Marks:** 2

```java
class Solution {
    static final long MOD = 1_000_000_007L;

    public int countBT(int h) {
        if (h <= 1) return 1;
        long prev2 = 1; 
        long prev1 = 1; 
        for (int i = 2; i <= h; i++) {
            long cur = (prev1 * prev1 % MOD + 2 * prev1 % MOD * prev2 % MOD) % MOD;
            prev2 = prev1;
            prev1 = cur;
        }
        return (int) prev1;
    }
}
```

*Generated on: 06/11/2026, 23:15:52*