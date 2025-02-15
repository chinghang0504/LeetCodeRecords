# [LeetCode Records](../../README.md) - Question 3452 Sum of Good Numbers

### Attempt 1: Use a for loop to search every number
```java
class Solution {
    public int sumOfGoodNumbers(int[] nums, int k) {
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            boolean isLeftGood = true;
            boolean isRightGood = true;
            if (i - k >= 0 && nums[i] <= nums[i - k]) {
                isLeftGood = false;
            }
            if (i + k < nums.length && nums[i] <= nums[i + k]) {
                isRightGood = false;
            }

            if (isLeftGood && isRightGood) {
                count += nums[i];
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.32 MB (Beats: 100.00%)

<br>
