## 01. Largest Sum Cycle

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/largest-sum-cycle--170645/1)

### Problem Description

**Task:** Given an array edge[] of size n, there are n cells numbered from 0 to n - 1. Each cell has at most one outgoing edge.For every cell i:edge[i] is the cell reached from i in one step.edge[i] = -1 means that cell i has no outgoing edge.A cycle is a sequence of cells where, by following the outgoing edges, we eventually return to the starting cell. The sum of a cycle is the sum of the indices of all cells in that cycle.Return the maximum cycle sum. If there is no cycle, return -1.Examples:Input: edge[] = [1, 2, 0, -1]Output: 3Explanation: There is only one cycle in the graph i.e. 0 - > 1 - > 2 - > 0. Sum of the cell index in that cycle = 0 + 1 + 2 = 3.Input: edge[] = [2, 0, -1, 2]Output: -1Explanation: There is no cycle in the graph. The edges are 1 - > 0 - > 2 < - 3. Hence, 2 has no outgoing edge, so no cycle exists.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-02 11:33:10
- **Status:** Correct
- **Marks:** 8

```java
class Solution {
    public int largestSumCycle(int[] edge) {
        int N = edge.length;
        int[] visited = new int[N];
        java.util.Arrays.fill(visited, -1);

        long best = -1;

        for (int i = 0; i < N; i++) {
            if (visited[i] != -1) continue;

            int cur = i;
            while (cur != -1 && visited[cur] == -1) {
                visited[cur] = i;
                cur = edge[cur];
            }

            if (cur != -1 && visited[cur] == i) {
                long sum = cur;
                int next = edge[cur];
                while (next != cur) {
                    sum += next;
                    next = edge[next];
                }
                best = Math.max(best, sum);
            }
        }
        return (int) best;
    }
}
```

*Generated on: 02/11/2026, 11:33:24*