## 01. Maximum Packages within Time

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/bird-and-maximum-fruit-gathering0509/1)

### Problem Description

**Task:** A delivery agent has to deliver packages at locations arranged in a line. The number of packages at the ith location is given by arr[i]. The agent can start at any location and can only visit consecutive locations.Visiting each location takes 1 unit of time.Given arr[] and totalTime, find the maximum number of packages the agent can deliver within totalTime.Examples:Input: arr[] = [2, 1, 3, 5, 0, 1, 4], totalTime = 3

#### Examples

##### Example 1

- **Output:**
```text
8
```
- **Explanation:** The agent can visit two consecutive locations. Starting from the second location, it delivers arr[1] + arr[2] = 6 + 2 = 8 packages. Starting from the fourth location gives arr[3] + arr[4] = 5 + 3 = 8 packages. Hence, the maximum is 8 packages.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (4)

#### Solution 1 (Java)

- **Submitted:** 2026-11-01 20:00:20
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    public int maxPackages(int[] arr, int totalTime) {
        int n = arr.length;
        if (totalTime > n) {
            totalTime = n;
        }

        int currentSum = 0;
        for (int i = 0; i < totalTime; i++) {
            currentSum += arr[i];
        }

        int maxSum = currentSum;

        for (int i = totalTime; i < n; i++) {
            currentSum += arr[i] - arr[i - totalTime];
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }
}
```

#### Solution 2 (Java)

- **Submitted:** 2026-11-01 19:58:45
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    public int maxPackages(int[] arr, int totalTime) {
        int n = arr.length;
        if (totalTime > n) {
            totalTime = n;
        }

        int currentSum = 0;
        for (int i = 0; i < totalTime; i++) {
            currentSum += arr[i];
        }

        int maxSum = currentSum;

        for (int i = totalTime; i < n; i++) {
            currentSum += arr[i] - arr[i - totalTime];
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }
}
```

#### Solution 3 (Java)

- **Submitted:** 2026-11-01 19:58:14
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    public int maxPackages(int[] arr, int totalTime) {
        int n = arr.length;
        if (totalTime > n) {
            totalTime = n;
        }

        int currentSum = 0;
        for (int i = 0; i < totalTime; i++) {
            currentSum += arr[i];
        }

        int maxSum = currentSum;

        for (int i = totalTime; i < n; i++) {
            currentSum += arr[i] - arr[i - totalTime];
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }
}
```

#### Solution 4 (Java)

- **Submitted:** 2026-11-01 19:45:14
- **Status:** Correct
- **Marks:** 2

```java
class Solution {
    public int maxPackages(int[] arr, int totalTime) {
        int n = arr.length;
        if (totalTime > n) {
            totalTime = n;
        }

        int currentSum = 0;
        for (int i = 0; i < totalTime; i++) {
            currentSum += arr[i];
        }

        int maxSum = currentSum;

        for (int i = totalTime; i < n; i++) {
            currentSum += arr[i] - arr[i - totalTime];
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }
}
```

*Generated on: 01/11/2026, 20:00:33*