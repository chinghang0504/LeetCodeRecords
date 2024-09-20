# [LeetCode Records](../../README.md) - Question 2340 Minimum Adjacent Swaps to Make a Valid Array

### Attempt 1: Find the indices of the minimum value and the maximum value
```java
class Solution {
    public int minimumSwaps(int[] nums) {
        int min = nums[0];
        int minIndex = 0;

        for (int i = minIndex + 1; i < nums.length; i++) {
            if (nums[i] < min) {
                min = nums[i];
                minIndex = i;
            }
        }

        int max = nums[nums.length - 1];
        int maxIndex = nums.length - 1;

        for (int i = maxIndex - 1; i >= 0; i--) {
            if (nums[i] > max) {
                max = nums[i];
                maxIndex = i;
            }
        }

        int count = minIndex + nums.length - maxIndex;
        return minIndex > maxIndex ? count - 2 : count - 1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 57.30 MB (Beats: 35.20%)

<br>
