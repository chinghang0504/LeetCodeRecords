# [LeetCode Records](../../README.md) - Question 2733 Neither Minimum nor Maximum

### Attempt 1: Record the min and max
```java
class Solution {
    public int findNonMinOrMax(int[] nums) {
        int max = nums[0];
        int min = nums[0];

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > max) {
                max = nums[i];
            } else if (nums[i] < min) {
                min = nums[i];
            }
        }

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != min && nums[i] != max) {
                return nums[i];
            }
        }

        return -1;
    }
}
```
- Runtime: 4 ms (Beats: 99.42%)
- Memory: 44.78 MB (Beats: 62.55%)

<br>
