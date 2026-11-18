## 01. XOR of Number Range

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-xor-of-numbers-from-l-to-r/1)

### Problem Description

**Task:** Given two integers l and r, find the bitwise XOR of all integers in the range [l, r] (both inclusive).Examples:Input: l = 4, r = 8

#### Examples

##### Example 1

- **Output:**
```text
5
```
- **Explanation:** The XOR of all integers from 5 to 9 is (5 xor 6 xor 7 xor 8 xor 9) = 5.Constraints:1 ≤ l ≤ r ≤ 10⁹

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-18 10:54:34
- **Status:** Correct
- **Marks:** 2

```java
class Solution {
    public int findXOR(int l, int r) {
        return computeXor(l - 1) ^ computeXor(r);
    }

    private int computeXor(int n) {
        int mod = n % 4;
        if (mod == 0) return n;
        if (mod == 1) return 1;
        if (mod == 2) return n + 1;
        return 0;
    }
}
```

*Generated on: 18/11/2026, 10:54:44*