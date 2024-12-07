# [LeetCode Records](../../README.md) - Question 3375 Minimum Operations to Make Array Values Equal to K

### Attempt 1: Count the number of different numbers
```java
class Solution {
    public int minOperations(int[] nums, int k) {
        Arrays.sort(nums);
        if (nums[0] < k) {
            return -1;
        }

        int count = 0;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i - 1] != nums[i]) {
                count++;
            }
        }

        return nums[0] == k ? count : count + 1;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.71 MB (Beats: 100.00%)

<br>
