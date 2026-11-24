## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/satisfy-the-equation5847/1)

### Problem Description

**Task:** Given an array arr[] of positive integers, find four indices a, b, c, and d such that arr[a] + arr[b] = arr[c] + arr[d], where a, b, c, d are all distinct indices.If multiple such quadruplets exist, return the one that is lexicographically smallest when the indices are considered in the order a, b, c, d. If no such quadruplet exists, return {-1, -1, -1, -1}. Ensure a < b and c < d, and the pair (a, b) is lexicographically smaller than the pair (c, d).Examples:Input: arr[] = [3, 4, 7, 1, 2, 9, 8]

#### Examples

##### Example 1

- **Output:**
```text
[-1, -1, -1, -1]
```
- **Explanation:** No two distinct pairs of indices produce the same sum.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-24 09:19:24
- **Status:** Correct
- **Marks:** 4

```java
import java.util.*;

class Solution {
    public ArrayList<Integer> findPairs(int[] arr) {
        int n = arr.length;
        Map<Integer, List<Integer>> map = new HashMap<>();
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                map.computeIfAbsent(arr[i] + arr[j], k -> new ArrayList<>())
                   .add(i * n + j);
            }
        }

        int[] best = null;

        for (List<Integer> list : map.values()) {
            if (list.size() < 2) continue;
            boolean found = false;
            for (int x = 0; x < list.size() && !found; x++) {
                int a = list.get(x) / n, b = list.get(x) % n;
                for (int y = x + 1; y < list.size(); y++) {
                    int c = list.get(y) / n, d = list.get(y) % n;
                    if (a != c && a != d && b != c && b != d) {
                        int[] cand = {a, b, c, d};
                        if (best == null || less(cand, best)) best = cand;
                        found = true;
                        break;
                    }
                }
            }
        }

        ArrayList<Integer> res = new ArrayList<>();
        if (best == null) {
            res.add(-1); res.add(-1); res.add(-1); res.add(-1);
        } else {
            for (int v : best) res.add(v);
        }
        return res;
    }

    private static boolean less(int[] p, int[] q) {
        for (int i = 0; i < 4; i++) {
            if (p[i] != q[i]) return p[i] < q[i];
        }
        return false;
    }
}
```

*Generated on: 24/11/2026, 09:19:36*