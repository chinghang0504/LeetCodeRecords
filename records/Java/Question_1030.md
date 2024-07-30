# [LeetCode Records](../../README.md) - Question 1030 Matrix Cells in Distance Order

### Attempt 1: Use a HashMap to save the positions
```java
class Solution {
    public int[][] allCellsDistOrder(int rows, int cols, int rCenter, int cCenter) {
        Map<Integer, List<int[]>> map = new HashMap<>();
        int maxDistance = rows + cols - 2;
        for (int i = 0; i <= maxDistance; i++) {
            map.put(i, new ArrayList<>());
        }

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                int distance = Math.abs(i - rCenter) + Math.abs(j - cCenter);
                map.get(distance).add(new int[]{i, j});
            }
        }

        int[][] answer = new int[rows * cols][2];
        int size = 0;
        for (int i = 0; i <= maxDistance; i++) {
            for (int[] position : map.get(i)) {
                answer[size] = position;
                size++;
            }
        }

        return answer;
    }
}
```
- Runtime: 11 ms (Beats: 80.11%)
- Memory: 46.12 MB (Beats: 53.78%)

<br>
