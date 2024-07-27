# [LeetCode Records](../../README.md) - Question 3038 Maximum Number of Operations With the Same Score I

### Attempt 1: Use a for loop
```java
class Solution {
    public int maxOperations(int[] nums) {
        int score = nums[0] + nums[1];
        int count = 1;

        for (int i = 2; i < nums.length - 1; i += 2) {
            int nextScore = nums[i] + nums[i + 1];
            if (score == nextScore) {
                count++;
            } else {
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.14 MB (Beats: 8.00%)

<br>
