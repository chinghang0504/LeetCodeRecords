# [LeetCode Records](../../README.md) - Question 3205 Maximum Array Hopping Score I

### Attempt 1: Use a nested loop
```java
class Solution {
    public int maxScore(int[] nums) {
        int[] accumulatedScores = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                accumulatedScores[j] = Math.max(accumulatedScores[j], accumulatedScores[i] + (j - i) * nums[j]);
            }
        }

        return accumulatedScores[nums.length - 1];
    }
}
```
- Runtime: 57 ms (Beats: 21.74%)
- Memory: 44.62 MB (Beats: 81.52%)

<br>
