# [LeetCode Records](../../README.md) - Question 2275 Largest Combination With Bitwise AND Greater Than Zero

### Attempt 1: Use an int[][] to store bits
```java
class Solution {
    public int largestCombination(int[] candidates) {
        int[][] bits = new int[candidates.length][32];

        for (int i = 0; i < candidates.length; i++) {
            int num = candidates[i];
            for (int j = 0; num > 0; j++) {
                bits[i][j] = num & 1;
                num >>>= 1;
            }
        }

        int maxCount = 0;
        for (int i = 0; i < 32; i++) {
            int count = 0;
            for (int j = 0; j < candidates.length; j++) {
                count += bits[j][i];
            }
            maxCount = Math.max(maxCount, count);
        }

        return maxCount;
    }
}
```
- Runtime: 55 ms (Beats: 13.99%)
- Memory: 79.00 MB (Beats: 6.99%)

<br>
