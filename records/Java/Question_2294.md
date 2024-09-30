# [LeetCode Records](../../README.md) - Question 2294 Partition Array Such That Maximum Difference Is K

### Attempt 1: Track the current maximum number
```java
class Solution {
    public int partitionArray(int[] nums, int k) {
        Arrays.sort(nums);

        int count = 1;
        int currMax = nums[0] + k;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > currMax) {
                count++;
                currMax = nums[i] + k;
            }
        }

        return count;
    }
}
```
- Runtime: 30 ms (Beats: 98.61%)
- Memory: 56.90 MB (Beats: 39.28%)

<br>
