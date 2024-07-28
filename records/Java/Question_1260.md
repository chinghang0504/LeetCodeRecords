# [LeetCode Records](../../README.md) - Question 1260 Shift 2D Grid

### Attempt 1: Use a helper function to shift the matrix
```java
class Solution {
    public List<List<Integer>> shiftGrid(int[][] grid, int k) {
        int m = grid.length;
        int n = grid[0].length;

        List<List<Integer>> answer = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            answer.add(new LinkedList<>());
        }

        for (int i = 0; i < m; i++) {
            List<Integer> list = answer.get(i);
            for (int j = 0; j < n; j++) {
                list.add(grid[i][j]);
            }
        }

        for (int i = 0; i < k; i++) {
            shift(answer, m);
        }

        return answer;
    }

    private void shift(List<List<Integer>> matrix, int m) {
        for (int i = 0; i < m - 1; i++) {
            int last = matrix.get(i).removeLast();
            matrix.get(i + 1).addFirst(last);
        }
        
        int last = matrix.get(m - 1).removeLast();
        matrix.get(0).addFirst(last);
    }
}
```
- Runtime: 8 ms (Beats: 30.69%)
- Memory: 45.94 MB (Beats: 8.58%)

<br>

### Attempt 2: Calculate the new index for every entry
```java
class Solution {
    public List<List<Integer>> shiftGrid(int[][] grid, int k) {
        int m = grid.length;
        int n = grid[0].length;

        int[][] matrix = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                int row = (i + (j + k) / n) % m;
                int col = (j + k) % n;
                matrix[row][col] = grid[i][j];
            }
        }

        List<List<Integer>> answer = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            List<Integer> list = new ArrayList<>();
            for (int j = 0; j < n; j++) {
                list.add(matrix[i][j]);
            }
            answer.add(list);
        }

        return answer;
    }
}
```
- Runtime: 5 ms (Beats: 84.16%)
- Memory: 45.06 MB (Beats: 89.44%)

<br>
