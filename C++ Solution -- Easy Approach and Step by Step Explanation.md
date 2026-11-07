## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/new-registration-system--150419/1)

### Problem Description

**Task:** Given an array of strings arr[]. The array represents first names of users, generate a unique username for each entry in the order it appears.Initially, consider all usernames present in the input array as reserved.If a username has not already been assigned to any previous user, keep it unchanged.Otherwise, append the smallest positive integer suffix that produces a username that has not been reserved or assigned to any previous user.Return the array of generated usernames.Examples:Input: arr[] = ["aba", "ab", "aba", "aba", "ab"]Output: ["aba", "ab", "aba1", "aba2", "ab1"]Explanation: The first occurrences of "aba" and "ab" are new, so they remain unchanged. The next "aba" is already used, so "aba1" is assigned. When "aba" appears again, "aba1" is already used, so "aba2" is assigned. Similarly, the second occurrence of "ab" becomes "ab1".Input: arr[] = ["a", "a", "a1", "a"]

#### Examples

##### Example 1

- **Output:**
```text
["aba1", "aba", "aba2"]
```
- **Explanation:** Initially, "aba1" and "aba" are reserved. The first occurrence of each retains its original name. For the second occurrence of "aba", "aba1" is already reserved, so "aba2" is assigned.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-07 23:16:56
- **Status:** Correct
- **Marks:** 2

```java
import java.util.*;

class Solution {
    public ArrayList<String> generateUsernames(String[] arr) {
        Set<String> reserved = new HashSet<>(Arrays.asList(arr));
        Set<String> assigned = new HashSet<>();
        Map<String, Integer> nextSuffix = new HashMap<>();
        ArrayList<String> result = new ArrayList<>();

        for (String name : arr) {
            if (!assigned.contains(name)) {
                assigned.add(name);
                result.add(name);
            } else {
                int k = nextSuffix.getOrDefault(name, 1);
                String candidate = name + k;
                while (reserved.contains(candidate) || assigned.contains(candidate)) {
                    k++;
                    candidate = name + k;
                }
                nextSuffix.put(name, k + 1);
                assigned.add(candidate);
                result.add(candidate);
            }
        }
        return result;
    }
}
```

*Generated on: 07/11/2026, 23:17:11*