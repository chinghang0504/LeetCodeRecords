# [LeetCode Records](../../README.md) - Question 153 Find Minimum in Rotated Sorted Array

### Attempt 1: Use binary search
```java
class Solution {
    public int findMin(int[] nums) {
        int low = 0;
        int high = nums.length - 1;

        while (true) {
            int middle = (low + high) / 2;
            
            if (nums[low] <= nums[middle]) {
                if (nums[middle] <= nums[high]) {
                    return nums[low];
                } else {
                    low = middle + 1;
                }
            } else {
                high = middle;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.08 MB (Beats: 32.25%)

<br>
