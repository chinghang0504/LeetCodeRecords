# [LeetCode Records](../../README.md) - Question 3417 Zigzag Grid Traversal With Skip

### Attempt 1: Simulate the process
```java
class Solution {
    public List<Integer> zigzagTraversal(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        List<Integer> ans = new ArrayList<>();

        int currI = 0;
        int currJ = 0;
        boolean isRight = true;
        while (currI < m) {
            ans.add(grid[currI][currJ]);

            if (isRight) {
                currJ += 2;
                if (currJ >= n) {
                    currJ = currJ == n ? n - 1 : n - 2;
                    currI++;
                    isRight = false;
                }
            } else {
                currJ -= 2;
                if (currJ <= 0) {
                    currJ = currJ == -1 ? 0 : 1;
                    currI++;
                    isRight = true;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.38 MB (Beats: 100.00%)

<br>
