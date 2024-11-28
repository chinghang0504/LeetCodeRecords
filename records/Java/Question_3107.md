# [LeetCode Records](../../README.md) - Question 3107 Minimum Operations to Make Median of Array Equal to K

### Attempt 1: Use Arrays.sort() to sort the array
```java
class Solution {
    public long minOperationsToMakeMedianK(int[] nums, int k) {
        long count = 0;

        Arrays.sort(nums);

        int startIndex = nums.length / 2;

        if (nums[startIndex] > k) {
            for (int i = startIndex; i >= 0; i--) {
                if (nums[i] > k) {
                    count += nums[i] - k;
                } else {
                    break;
                }
            }
        } else if (nums[startIndex] < k) {
            for (int i = startIndex; i < nums.length; i++) {
                if (nums[i] < k) {
                    count += k - nums[i];
                } else {
                    break;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 29 ms (Beats: 80.00%)
- Memory: 62.12 MB (Beats: 91.72%)

<br>
