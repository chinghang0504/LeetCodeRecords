# [LeetCode Records](../../README.md) - Question 120 Triangle

### Attempt 1: Use the source list to accumulate
```java
class Solution {
    public int minimumTotal(List<List<Integer>> triangle) {
        int triangleSize = triangle.size();
        List<Integer> prevRow = triangle.get(0);

        for (int i = 1; i < triangleSize; i++) {
            List<Integer> row = triangle.get(i);
            for (int j = 0; j < i + 1; j++) {
                if (j == 0) {
                    row.set(j, row.get(j) + prevRow.get(j));
                } else if (j == i) {
                    row.set(j, row.get(j) + prevRow.get(j - 1));
                } else {
                    row.set(j, row.get(j) + Math.min(prevRow.get(j - 1), prevRow.get(j)));
                }
            }
            prevRow = row;
        }

        int min = prevRow.get(0);
        for (int i = 1; i < triangleSize; i++) {
            min = Math.min(min, prevRow.get(i));
        }

        return min;
    }
}
```
- Runtime: 5 ms (Beats: 34.74%)
- Memory: 43.96 MB (Beats: 63.69%)

<br>

### Attempt 2: Use an int array to accumulate
```java
class Solution {
    public int minimumTotal(List<List<Integer>> triangle) {
        int triangleSize = triangle.size();
        int[][] saved = new int[triangleSize][triangleSize];
        saved[0][0] = triangle.get(0).get(0);

        for (int i = 1; i < triangleSize; i++) {
            List<Integer> row = triangle.get(i);
            for (int j = 0; j < i + 1; j++) {
                if (j == 0) {
                    saved[i][j] = row.get(j) + saved[i - 1][j];
                } else if (j == i) {
                    saved[i][j] = row.get(j) + saved[i - 1][j - 1];
                } else {
                    saved[i][j] = row.get(j) + Math.min(saved[i - 1][j - 1], saved[i - 1][j]);
                }
            }
        }

        int min = saved[triangleSize - 1][0];
        for (int i = 1; i < triangleSize; i++) {
            min = Math.min(min, saved[triangleSize - 1][i]);
        }

        return min;
    }
}
```
- Runtime: 3 ms (Beats: 66.18%)
- Memory: 43.87 MB (Beats: 72.32%)

<br>
