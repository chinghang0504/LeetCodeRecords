# [LeetCode Records](../../README.md) - Question 2368 Reachable Nodes With Restrictions

### Attempt 1: Use an ArrayList to store the edges, a HashSet to store the restricted nodes, and a boolean[] to store the checked nodes
```java
class Solution {
    public int reachableNodes(int n, int[][] edges, int[] restricted) {
        List<List<Integer>> lists = new ArrayList<>(n);
        for (int i = 0; i < n; i++) {
            lists.add(new ArrayList<>());
        }
        for (int[] edge : edges) {
            lists.get(edge[0]).add(edge[1]);
            lists.get(edge[1]).add(edge[0]);
        }

        Set<Integer> restrictedNodes = new HashSet<>();
        for (int restrictedNode : restricted) {
            restrictedNodes.add(restrictedNode);
        }

        boolean[] checkedNodes = new boolean[n];
        checkNode(lists, restrictedNodes, checkedNodes, 0);

        int count = 0;
        for (boolean checkedNode : checkedNodes) {
            if (checkedNode) {
                count++;
            }
        }

        return count;
    }

    private void checkNode(List<List<Integer>> lists, Set<Integer> restrictedNodes, boolean[] checkedNodes, int node) {
        if (checkedNodes[node]) {
            return;
        } else if (restrictedNodes.contains(node)) {
            return;
        }

        checkedNodes[node] = true;

        for (int nextNode : lists.get(node)) {
            checkNode(lists, restrictedNodes, checkedNodes, nextNode);
        }
    }
}
```
- Runtime: 54 ms (Beats: 82.71%)
- Memory: 116.50 MB (Beats: 46.05%)

<br>
