# [LeetCode Records](../../README.md) - Question 1380 Lucky Numbers in a Matrix

### Attempt 1: Use two nested loops
```java
class Solution {
    public List<Integer> luckyNumbers (int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        Set<Integer> set = new HashSet<>();

        for (int i = 0; i < m; i++) {
            int min = matrix[i][0];
            for (int j = 1; j < n; j++) {
                min = Math.min(min, matrix[i][j]);
            }
            set.add(min);
        }

        List<Integer> result = new ArrayList<>();
        for (int j = 0; j < n; j++) {
            int max = matrix[0][j];
            for (int i = 1; i < m; i++) {
                max = Math.max(max, matrix[i][j]);
            }

            if (set.contains(max)) {
                result.add(max);
            }
        }

        return result;
    }
}
```
- Runtime: 3 ms (Beats: 45.52%)
- Memory: 45.42 MB (Beats: 9.20%)

<br>
