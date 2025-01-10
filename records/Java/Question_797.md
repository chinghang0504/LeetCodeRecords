# [LeetCode Records](../../README.md) - Question 797 All Paths From Source to Target

### Attempt 1: Use recursion to add a current index and remove the current index when return
```java
class Solution {

    private int[][] graph;
    private List<List<Integer>> ans;

    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        this.graph = graph;
        ans = new ArrayList<>();

        getAllPaths(new ArrayList<>(), 0);

        return ans;
    }

    private void getAllPaths(List<Integer> list, int currIndex) {
        list.addLast(currIndex);

        if (currIndex == graph.length - 1) {
            ans.addLast(new ArrayList<>(list));
            list.removeLast();
            return;
        }

        for (int nextIndex : graph[currIndex]) {
            getAllPaths(list, nextIndex);
        }

        list.removeLast();
    }
}
```
- Runtime: 1 ms (Beats: 99.83%)
- Memory: 46.26 MB (Beats: 72.33%)

<br>
