# [LeetCode Records](../../README.md) - Question 747 Largest Number At Least Twice of Others

### Attempt 1: 
```java
class Solution {
    public int dominantIndex(int[] nums) {
        int maxNum = nums[0];
        int maxIndex = 0;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > maxNum) {
                maxNum = nums[i];
                maxIndex = i;
            }
        }

        int maxHalf = maxNum / 2;
        for (int i = 0; i < maxIndex; i++) {
            if (nums[i] > maxHalf) {
                return -1;
            }
        }
        for (int i = maxIndex + 1; i < nums.length; i++) {
            if (nums[i] > maxHalf) {
                return -1;
            }
        }
        return maxIndex;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.15 MB (Beats: 79.47%)

<br>
