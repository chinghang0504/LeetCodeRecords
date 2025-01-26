# [LeetCode Records](../../README.md) - Question 3432 Count Partitions with Even Sum Difference

### Attempt 1: Get the total sum first
```java
class Solution {
    public int countPartitions(int[] nums) {
        int rightSum = 0;
        for (int num : nums) {
            rightSum += num;
        }

        int count = 0;
        int leftSum = 0;
        for (int i = 0; i < nums.length - 1; i++) {
            leftSum += nums[i];
            rightSum -= nums[i];
            if ((leftSum - rightSum) % 2 == 0) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.90 MB (Beats: -%)

<br>
