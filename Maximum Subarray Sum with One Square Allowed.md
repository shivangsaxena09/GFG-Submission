## 01. Maximum Subarray Sum with One Square Allowed

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-sum-subarray--143510/1)

### Problem Description

**Task:** Given an integer array arr[], find the maximum subarray sum by squaring at most one element.Examples:Input: arr[] = [-1, -2, 3, -2, 3]Output: 10Explanation: The subarray {3, -2, 3} with squaring -2 will give the maximum sum as 3 + 4 + 3 = 10.Input: arr[] = [-4, -4, -2, 5, 2, -1]Output: 27Explanation: The subarray {5, 2} with squaring 5 will give a maximum sum of 25 + 2 = 27.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-01 20:02:08
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
    public int maximumSubarray(int[] arr) {
        int n = arr.length;
        if (n == 0) return 0;

        long prevNormal = arr[0];
        long prevSquare = (long) arr[0] * arr[0];
        long globalMax = Math.max(prevNormal, prevSquare);

        for (int i = 1; i < n; i++) {
            long currVal = arr[i];
            long currValSq = (long) arr[i] * arr[i];
            long currNormal = Math.max(currVal, prevNormal + currVal);
            long currSquare = Math.max(currValSq, Math.max(prevNormal + currValSq, prevSquare + currVal));

            globalMax = Math.max(globalMax, Math.max(currNormal, currSquare));

            prevNormal = currNormal;
            prevSquare = currSquare;
        }

        return (int) globalMax;
    }
}
```

*Generated on: 01/11/2026, 20:02:13*