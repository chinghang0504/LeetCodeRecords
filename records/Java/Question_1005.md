# [LeetCode Records](../../README.md) - Question 1005 Maximize Sum Of Array After K Negations

### Attempt 1: Use Arrays.sort() in each operation
```java
class Solution {
    public int largestSumAfterKNegations(int[] nums, int k) {
        for (int i = 0; i < k; i++) {
            Arrays.sort(nums);
            nums[0] *= -1;
        }

        int sum = 0;
        for (int num : nums) {
            sum += num;
        }

        return sum;
    }
}
```
- Runtime: 18 ms (Beats: 12.97%)
- Memory: 42.25 MB (Beats: 48.71%)

<br>
