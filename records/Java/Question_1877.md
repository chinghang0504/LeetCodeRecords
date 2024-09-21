# [LeetCode Records](../../README.md) - Question 1877 Minimize Maximum Pair Sum in Array

### Attempt 1: Use Arrays.sort() to sort the array
```java
class Solution {
    public int minPairSum(int[] nums) {
        Arrays.sort(nums);

        int max = 0;
        for (int i = 0; i < nums.length; i++) {
            max = Math.max(max, nums[i] + nums[nums.length - i - 1]);
        }

        return max;
    }
}
```
- Runtime: 53 ms (Beats: 43.60%)
- Memory: 58.01 MB (Beats: 76.56%)

<br>
