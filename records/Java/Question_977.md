# [LeetCode Records](../../README.md) - Question 977 Squares of a Sorted Array

### Attempt 1: Use the Arrays.sort()
```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        for (int i = 0; i < nums.length; i++) {
            nums[i] *= nums[i];
        }

        Arrays.sort(nums);

        return nums;
    }
}
```
- Runtime: 7 ms (Beats: 48.13%)
- Memory: 47.11 MB (Beats: 38.80%)

<br>
