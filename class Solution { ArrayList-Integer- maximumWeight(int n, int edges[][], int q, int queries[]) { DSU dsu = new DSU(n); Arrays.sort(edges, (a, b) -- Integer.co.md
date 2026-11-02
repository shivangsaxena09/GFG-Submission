## 01. class Solution { ArrayList<Integer> maximumWeight(int n, int edges[][], int q, int queries[]) { DSU dsu = new DSU(n); Arrays.sort(edges, (a, b) -> Integer.compare(a[2], b[2])); TreeMap<Integer, Integer> map = new TreeMap<>(); int prevPaths = 0; for(int[] edge: edges){ int union = dsu.union(edge[0], edge[1]); int paths = prevPaths + union; map.put(edge[2], paths); prevPaths = paths; } ArrayList<Integer> ans = new ArrayList<>(); for(int i = 0; i < q; i++){ int maxPaths = 0; Map.Entry<Integer, Integer> val = map.floorEntry(queries[i]); if(val == null) ans.add(0); else ans.add(val.getValue()); } return ans; }}

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/possible-paths--141628/1)

### Problem Description

**Task:** Given a weighted tree with n nodes, numbered from 1 to n and n - 1 edges, where each edge is represented as [u, v, w] indicating an edge between nodes u and v with weight w.You are also given an array queries[], where each queries[i] represents a maximum allowed edge weight.For each query x, find the number of distinct paths in the tree such that the maximum edge weight along the path is less than or equal to x.Return an array containing the number of valid paths for each query.Note: A path from node u to node v and the path from node v to node u are considered the same path. A path must contain at least one edge. A path from a node to itself is not considered.Examples:Input: n = 3, edges[][] = [[1, 2, 1], [2, 3, 4]], queries[] = [3]

#### Examples

##### Example 1

- **Output:**
```text
[1, 3, 4]
```
- **Explanation:** For x = 1, only the edge [2, 3, 1] satisfies the condition. Therefore, the only valid path is 2 - > 3, giving an answer of 1. For x = 3, the edges [2, 3, 1] and [1, 2, 3] can be used. They form three valid paths: 1 - > 2, 2 - > 3, and 1 - > 3. For x = 5, the edges with weights 1, 3, and 4 can be used. They form four valid paths: 1 - > 2, 2 - > 3, 1 - > 3, and 5 - > 7.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(nlogn + qlogn)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-03 01:38:19
- **Status:** Correct
- **Marks:** 8

```java
import java.util.*;

class Solution {
    class DSU {
        int[] parent;
        int[] size;
        long totalPaths;

        public DSU(int n) {
            parent = new int[n + 1];
            size = new int[n + 1];
            for (int i = 1; i <= n; i++) {
                parent[i] = i;
                size[i] = 1;
            }
            totalPaths = 0;
        }

        public int find(int i) {
            if (parent[i] == i)
                return i;
            return parent[i] = find(parent[i]);
        }

        public void union(int u, int v) {
            int rootU = find(u);
            int rootV = find(v);
            if (rootU != rootV) {
                totalPaths -= (long) size[rootU] * (size[rootU] - 1) / 2;
                totalPaths -= (long) size[rootV] * (size[rootV] - 1) / 2;

                if (size[rootU] < size[rootV]) {
                    parent[rootU] = rootV;
                    size[rootV] += size[rootU];
                    totalPaths += (long) size[rootV] * (size[rootV] - 1) / 2;
                } else {
                    parent[rootV] = rootU;
                    size[rootU] += size[rootV];
                    totalPaths += (long) size[rootU] * (size[rootU] - 1) / 2;
                }
            }
        }
    }

    class Query implements Comparable<Query> {
        int weight;
        int index;

        public Query(int weight, int index) {
            this.weight = weight;
            this.index = index;
        }

        @Override
        public int compareTo(Query other) {
            return Integer.compare(this.weight, other.weight);
        }
    }

    public ArrayList<Integer> maximumWeight(int n, int[][] edges, int[] queries) {
        Arrays.sort(edges, (a, b) -> Integer.compare(a[2], b[2]));

        int qLen = queries.length;
        Query[] sortedQueries = new Query[qLen];
        for (int i = 0; i < qLen; i++) {
            sortedQueries[i] = new Query(queries[i], i);
        }
        Arrays.sort(sortedQueries);

        ArrayList<Integer> ans = new ArrayList<>(Collections.nCopies(qLen, 0));
        DSU dsu = new DSU(n);
        int edgeIndex = 0;
        int m = edges.length;

        for (int i = 0; i < qLen; i++) {
            while (edgeIndex < m && edges[edgeIndex][2] <= sortedQueries[i].weight) {
                dsu.union(edges[edgeIndex][0], edges[edgeIndex][1]);
                edgeIndex++;
            }
            ans.set(sortedQueries[i].index, (int) dsu.totalPaths);
        }

        return ans;
    }
}
```

*Generated on: 03/11/2026, 01:38:33*