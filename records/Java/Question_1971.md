# [LeetCode Records](../../README.md) - Question 1971 Find if Path Exists in Graph

### Attempt 1: Use a ArrayList with HashSet to record the edges
```java
class Solution {
    public boolean validPath(int n, int[][] edges, int source, int destination) {
        List<Set<Integer>> paths = new ArrayList<>();
        boolean[] reachedPoints = new boolean[n];

        for (int i = 0; i < n; i++) {
            paths.add(new HashSet<>());
        }

        for (int[] edge : edges) {
            paths.get(edge[0]).add(edge[1]);
            paths.get(edge[1]).add(edge[0]);
        }

        return canReachGoal(n, paths, reachedPoints, source, destination);
    }

    private boolean canReachGoal(int n, List<Set<Integer>> paths, boolean[] reachedPoints, int curr, int destination) {
        if (curr == destination) {
            return true;
        } else if (reachedPoints[curr]) {
            return false;
        }

        reachedPoints[curr] = true;
        for (int i : paths.get(curr)) {
            if (canReachGoal(n, paths, reachedPoints, i, destination)) {
                return true;
            }
        }
        
        return false;
    }
}
```
- Runtime: 280 ms (Beats: 17.44%)
- Memory: 217.29 MB (Beats: 5.33%)

<br>
