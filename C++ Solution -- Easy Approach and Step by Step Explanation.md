## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1)

### Problem Description

**Task:** Given an integer x and an array of integers, arr[]. Find the length of the smallest subarray whose sum is strictly greater than x. If no such subarray exists, return 0.Examples:Input: x = 51, arr[] = [1, 4, 45, 6, 0, 19]

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray has a sum greater than 100. Hence, the answer is 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-21 18:39:09
- **Status:** Correct
- **Marks:** 2

```java
class Solution {
    public int smallestSubWithSum(int[] arr, int x) {
        int n = arr.length;
        int left = 0;
        long sum = 0;
        int minLen = Integer.MAX_VALUE;

        for (int right = 0; right < n; right++) {
            sum += arr[right];

            while (sum > x) {
                minLen = Math.min(minLen, right - left + 1);
                sum -= arr[left];
                left++;
            }
        }

        return minLen == Integer.MAX_VALUE ? 0 : minLen;
    }
}
```

*Generated on: 21/11/2026, 18:39:24*