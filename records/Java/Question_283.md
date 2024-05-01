# [LeetCode Records](../../README.md) - Question 283 Move Zeroes

### Attempt 1: 
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int curr = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[curr++] = nums[i];
            }
        }

        int zeroCount = nums.length - curr;
        for (int i = 0; i < zeroCount; i++) {
            nums[nums.length - 1 - i] = 0;
        }
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.48 MB (Beats: 95.93%)

<br>
