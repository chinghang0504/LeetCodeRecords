# [LeetCode Records](../../README.md) - Question 3192 Minimum Operations to Make Binary Array Elements Equal to One II

### Attempt 1: Start from the first zero and count the number of different groups
```java
class Solution {
    public int minOperations(int[] nums) {
        int count = 0;

        int i = 0;
        while (i < nums.length) {
            while (i < nums.length && nums[i] == 1) {
                i++;
            }
            if (i >= nums.length) {
                return count;
            }
            count++;

            while (i < nums.length && nums[i] == 0) {
                i++;
            }
            if (i >= nums.length) {
                return count;
            }
            count++;
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 99.18%)
- Memory: 57.04 MB (Beats: 42.80%)

<br>
