# [LeetCode Records](../../README.md) - Question 75 Sort Colors

### Attempt 1: Count the numbers first
```java
class Solution {
    public void sortColors(int[] nums) {
        int count_0 = 0, count_1 = 0;
        for (int i : nums) {
            if (i == 0) {
                count_0++;
            } else if (i == 1) {
                count_1++;
            }
        }

        int i = 0;
        for (; i < count_0; i++) {
            nums[i] = 0;
        }
        for (; i < count_0 + count_1; i++) {
            nums[i] = 1;
        }
        for (; i < nums.length; i++) {
            nums[i] = 2;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.43 MB (Beats: 89.17%)

<br>
