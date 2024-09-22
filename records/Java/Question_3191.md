# [LeetCode Records](../../README.md) - Question 3191 Minimum Operations to Make Binary Array Elements Equal to One I

### Attempt 1: Flip if the first element is 0
```java
class Solution {
    public int minOperations(int[] nums) {
        int count = 0;

        for (int i = 0; i < nums.length - 2; i++) {
            if (nums[i] == 0) {
                flip(nums, i);
                count++;
            }
        }

        return nums[nums.length - 2] == 1 && nums[nums.length - 1] == 1 ? count : -1;
    }

    private void flip(int[] nums, int start) {
        for (int i = 0; i < 3; i++) {
            nums[start + i] = nums[start + i] == 0 ? 1 : 0;
        }
    }
}
```
- Runtime: 8 ms (Beats: 38.80%)
- Memory: 57.32 MB (Beats: 45.90%)

<br>
