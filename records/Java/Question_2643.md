# [LeetCode Records](../../README.md) - Question 2643 Row With Maximum Ones

### Attempt 1: Use a nested loop
```java
class Solution {
    public int[] rowAndMaximumOnes(int[][] mat) {
        int max = 0;
        int maxIndex = 0;

        for (int i = 0; i < mat.length; i++) {
            int sum = 0;

            for (int num : mat[i]) {
                sum += num;
            }

            if (sum > max) {
                max = sum;
                maxIndex = i;
            }
        }

        return new int[]{maxIndex, max};
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 46.46 MB (Beats: 49.03%)

<br>
