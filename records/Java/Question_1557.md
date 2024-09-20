# [LeetCode Records](../../README.md) - Question 1557 Minimum Number of Vertices to Reach All Nodes

### Attempt 1: Use a boolean[] to record which nodes have incoming edges
```java
class Solution {
    public List<Integer> findSmallestSetOfVertices(int n, List<List<Integer>> edges) {
        boolean[] inComingNodes = new boolean[n];

        for (List<Integer> edge : edges) {
            int toNode = edge.get(1);
            inComingNodes[toNode] = true;
        }

        List<Integer> ans = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            if (!inComingNodes[i]) {
                ans.add(i);
            }
        }

        return ans;
    }
}
```
- Runtime: 8 ms (Beats: 97.90%)
- Memory: 82.29 MB (Beats: 95.05%)

<br>
