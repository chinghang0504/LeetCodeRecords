# [LeetCode Records](../../README.md) - Question 2574 Left and Right Sum Differences

### Attempt 1: Use three int[]
```java
class Solution {
    public int[] leftRightDifference(int[] nums) {
        int[] leftSum = new int[nums.length];
        for (int i = 1; i < nums.length; i++) {
            leftSum[i] = leftSum[i - 1] + nums[i - 1];
        }

        int[] rightSum = new int[nums.length];
        for (int i = nums.length - 2; i >= 0; i--) {
            rightSum[i] = rightSum[i + 1] + nums[i + 1];
        }

        int[] answer = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            answer[i] = Math.abs(leftSum[i] - rightSum[i]);
        }

        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 98.83%)
- Memory: 44.73 MB (Beats: 17.35%)

<br>
