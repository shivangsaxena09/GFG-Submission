## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-the-characters1821/1)

### Problem Description

**Task:** Given a string s and an integer k, count the number of distinct characters that appear in exactly k groups in the string.A group is defined as one or more consecutive occurrences of the same character. For example, in the string "aaabbcca", the groups are "aaa", "bb", "cc" and "a".Examples:Input: s = "abc", k = 1Output: 3Explanation: The characters 'a', 'b' and 'c' each appear in exactly one group.Input: s = "geeksforgeeks", k = 2Output: 4Explanation: The characters 'g', 'e', 'k' and 's' each appear in exactly two groups.Input: s = "aaaaa", k = 2Output: 0Explanation: The character 'a' appears in only one group, so no character appears in exactly two groups.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-09 20:29:03
- **Status:** Correct
- **Marks:** 2

```java
class Solution {
    public int getCount(String s, int k) {
        int[] groups = new int[26];

        for (int i = 0; i < s.length(); i++) {
            if (i == 0 || s.charAt(i) != s.charAt(i - 1)) {
                groups[s.charAt(i) - 'a']++;
            }
        }

        int ans = 0;
        for (int g : groups) {
            if (g == k) ans++;
        }
        return ans;
    }
}
```

*Generated on: 09/11/2026, 20:29:18*