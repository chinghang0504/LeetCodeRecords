# [LeetCode Records](../../README.md) - Question 2679 Sum in a Matrix

### Attempt 1: Use Arrays.sort() to sort the arrays of each row
```java
class Solution {
    public int matrixSum(int[][] nums) {
        int m = nums.length;
        int n = nums[0].length;

        for (int i = 0; i < m; i++) {
            Arrays.sort(nums[i]);
        }

        int sum = 0;
        for (int j = 0; j < n; j++) {
            int max = nums[0][j];
            for (int i = 1; i < m; i++) {
                max = Math.max(max, nums[i][j]);
            }
            sum += max;
        }

        return sum;
    }
}
```
- Runtime: 13 ms (Beats: 100.00%)
- Memory: 69.96 MB (Beats: 57.54%)

<br>
