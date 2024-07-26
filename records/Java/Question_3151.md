# [LeetCode Records](../../README.md) - Question 3151 Special Array I

### Attempt 1: Compare the previous values
```java
class Solution {
    public boolean isArraySpecial(int[] nums) {
        boolean prevIsOdd = nums[0] % 2 == 1;

        for (int i = 1; i < nums.length; i++) {
            boolean isOdd = nums[i] % 2 == 1;
            if (prevIsOdd == isOdd) {
                return false;
            }

            prevIsOdd = isOdd;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.19 MB (Beats: 46.94%)

<br>
