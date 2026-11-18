## 01. MemoIzation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/matrix-chain-multiplication0303/1)

### Problem Description

**Task:** Given an array arr[] which represents the dimensions of a sequence of matrices where the i^th matrix has the dimensions (arr[i-1] x arr[i]) for i >= 1, find the most efficient way to multiply these matrices together. The efficient way is the one that involves the least number of multiplications.Examples:Input: arr[] = [2, 1, 3, 4]

#### Examples

##### Example 1

- **Output:**
```text
0Explanation: As there is only one matrix so, there is no cost of multiplication.
```
- **Explanation:** There are 4 matrices of dimensions 1 × 2, 2 × 3, 3 × 4, 4 × 3. Let this 4 input matrices be M1, M2, M3 and M4. The minimum number of multiplications are obtained by ((M1 x M2) x M3) x M4). The minimum number is (1 x 2 x 3) + (1 x 3 x 4) + (1 x 4 x 3) = 30.Input: arr[] = [3, 4]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^3)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (2)

#### Solution 1 (Java)

- **Submitted:** 2026-11-18 17:18:15
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    static int matrixMultiplication(int arr[]) {
        int n = arr.length;
        int[][] dp = new int[n][n];
        for (int len = 2; len < n; len++) {
            for (int i = 1; i + len - 1 < n; i++) {
                int j = i + len - 1;
                dp[i][j] = Integer.MAX_VALUE;
                for (int k = i; k < j; k++) {
                    int cost = dp[i][k] + dp[k + 1][j] + arr[i - 1] * arr[k] * arr[j];
                    if (cost < dp[i][j]) {
                        dp[i][j] = cost;
                    }
                }
            }
        }
        return dp[1][n - 1];
    }
}
```

#### Solution 2 (Java)

- **Submitted:** 2026-11-18 17:15:55
- **Status:** Correct
- **Marks:** 8

```java
class Solution {
    static int matrixMultiplication(int arr[]) {
        int n = arr.length;
        int[][] dp = new int[n][n];
        for (int i = 1; i < n; i++) {
            dp[i][i] = 0;
        }
        for (int L = 2; L < n; L++) {
            for (int i = 1; i < n - L + 1; i++) {
                int j = i + L - 1;
                dp[i][j] = Integer.MAX_VALUE;
                for (int k = i; k < j; k++) {
                    int cost = dp[i][k] + dp[k + 1][j] + arr[i - 1] * arr[k] * arr[j];
                    if (cost < dp[i][j]) {
                        dp[i][j] = cost;
                    }
                }
            }
        }

        return dp[1][n - 1];
    }
}
```

*Generated on: 18/11/2026, 17:18:34*