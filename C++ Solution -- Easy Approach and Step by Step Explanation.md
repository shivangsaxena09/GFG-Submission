## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sum-of-all-sub-sequences-of-a-number3437/1)

### Problem Description

**Task:** Given a string s which consists of digits, find sum of all digits across all non-empty subsequences of s.Note: Since the answer can be very large, return it modulo 10⁹ + 7.Examples:Input: s = "123"

#### Examples

##### Example 1

- **Output:**
```text
24
```
- **Explanation:** The non-empty subsequences are: [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]. The sum of all digits in these subsequences is: 1 + 2 + 3 + (1 + 2) + (1 + 3) + (2 + 3) + (1 + 2 + 3) = 24.

##### Example 2

- **Input:**
```text
s = "405"
```
- **Output:**
```text
36
```
- **Explanation:** The non-empty subsequences are: [4], [0], [5], [4, 0], [4, 5], [0, 5], [4, 0, 5]. The sum of all digits in these subsequences is 36.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-15 23:22:56
- **Status:** Correct
- **Marks:** 2

```java
class Solution {
    public int subsequenceSum(String s) {
        final long MOD = 1_000_000_007L;
        int n = s.length();

        long digitSum = 0;
        for (int i = 0; i < n; i++) {
            digitSum += s.charAt(i) - '0';
        }
        digitSum %= MOD;

        long result = digitSum * power(2, n - 1, MOD) % MOD;
        return (int) result;
    }

    private long power(long base, long exp, long mod) {
        long res = 1;
        base %= mod;
        while (exp > 0) {
            if ((exp & 1) == 1) {
                res = res * base % mod;
            }
            base = base * base % mod;
            exp >>= 1;
        }
        return res;
    }
}
```

*Generated on: 15/11/2026, 23:23:12*