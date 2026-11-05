## 01. Minimum Days

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-days--170646/1)

### Problem Description

**Task:** Given a string s of length n containing only lowercase English letters, and a permutation array p[] of length n containing integers from 0 to n - 1. On the (i + 1)th day, the character at index p[i] in the string is replaced with '?'. For example:On day 1, replace s[p[0]] with '?'.On day 2, replace s[p[1]] with '?'.On day 3, replace s[p[2]] with '?'.And so on.Find the minimum number of days required so that no two adjacent characters in s are equal, unless at least one of them is '?'.Formally, for every index i (0 <= i < n - 1), the string must satisfy: If s[i] ! = '?' and s[i+1] ! = '?', then s[i] ! = s[i+1].Examples:Input: s = "aabb", p = [2, 1, 3, 0]

#### Examples

##### Example 1

- **Output:**
```text
0 The initial string "abca" already satisfies the condition without replacing any characters.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n) [Note: For CPP - O(1)]

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-05 17:17:26
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
    public int getMinimumDays(String s, int[] p) {
        int n = s.length();
                int[] day = new int[n];
                for (int i = 0; i < n; i++) {
                    day[p[i]] = i + 1;
                }
                int ans = 0;
                for (int i = 0; i + 1 < n; i++) {
                    if (s.charAt(i) == s.charAt(i + 1)) {
                        ans = Math.max(ans, Math.min(day[i], day[i + 1]));
                    }
                }
                return ans;
        
    }
}
```

*Generated on: 05/11/2026, 17:17:56*