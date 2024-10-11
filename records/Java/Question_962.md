# [LeetCode Records](../../README.md) - Question 962 Maximum Width Ramp

### Attempt 1: Use an int[][] to store the number and the index key-value pairs
```java
class Solution {
    public int maxWidthRamp(int[] nums) {
        int[][] ranks = new int[nums.length][2];
        for (int i = 0; i < nums.length; i++) {
            ranks[i][0] = nums[i];
            ranks[i][1] = i;
        }

        Arrays.sort(ranks, (r1, r2) -> r1[0] != r2[0] ? r1[0] - r2[0] : r1[1] - r2[1]);

        int maxIndex = 0;
        int maxWidth = 0;
        for (int i = ranks.length - 1; i >= 0; i--) {
            if (ranks[i][1] > maxIndex) {
                maxIndex = ranks[i][1];
            } else {
                maxWidth = Math.max(maxWidth, maxIndex - ranks[i][1]);
            }
        }

        return maxWidth;
    }
}
```
- Runtime: 39 ms (Beats: 12.57%)
- Memory: 54.34 MB (Beats: 53.21%)

<br>
