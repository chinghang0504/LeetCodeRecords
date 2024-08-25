# [LeetCode Records](../../README.md) - Question 3264 Final Array State After K Multiplication Operations I

### Attempt 1: Use a nested loop
```java
class Solution {
    public int[] getFinalState(int[] nums, int k, int multiplier) {
        for (int t = 0; t < k; t++) {
            int min = nums[0];
            int minIndex = 0;

            for (int i = 1; i < nums.length; i++) {
                if (nums[i] < min) {
                    min = nums[i];
                    minIndex = i;
                }
            }

            nums[minIndex] *= multiplier;
        }

        return nums;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.66 MB (Beats: 100.00%)

<br>
