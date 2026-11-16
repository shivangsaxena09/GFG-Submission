## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/k-th-missing-element-in-natural-numbers/1)

### Problem Description

**Task:** Given an array arr[] of distinct positive integers and a positive integer k. Consider an infinite sequence of natural numbers starting from 1. The task is to remove all elements present in arr[] from this sequence.Find the k-th smallest number in the remaining sequence.Note: Your solution must run in O(1) auxiliary space.Examples:Input: arr[] = [1, 9, 5, 2], k = 6Output: 10Explanation: After removing [1, 2, 5, 9] from the natural numbers, the remaining sequence is: 3, 4, 6, 7, 8, 10, 11, .... and so on. The 6th number in this sequence is 10, so the answer is 10.Input: arr[] = [1, 2, 3, 4], k = 1Output: 5Explanation: After removing [1, 2, 3, 4] from the natural numbers, the remaining sequence is: 5, 6, 7, .... and so on. The 1st number in the sequence is 5, so the answer is 5.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-16 09:13:20
- **Status:** Correct
- **Marks:** 4

```java
import java.util.Arrays;

class Solution {
    public int findKthSmall(int[] arr, int k) {
        Arrays.sort(arr);
        int low = 0, high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            int missingCount = arr[mid] - (mid + 1);

            if (missingCount >= k) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }

        return low + k;
    }
}
```

*Generated on: 16/11/2026, 09:13:36*