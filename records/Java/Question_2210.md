# [LeetCode Records](../../README.md) - Question 2210 Count Hills and Valleys in an Array

### Attempt 1: Use a boolean variable to track if it is going up or down
```java
class Solution {
    public int countHillValley(int[] nums) {
        int prev1 = nums[0];

        int i = 1;
        while (i < nums.length && nums[i] == prev1) {
            i++;
        }
        if (i == nums.length) {
            return 0;
        }

        int prev2 = nums[i];
        boolean isUp = prev2 > prev1;
        int count = 0;

        i++;
        while (true) {
            while (i < nums.length && nums[i] == prev2) {
                i++;
            }

            if (i == nums.length) {
                break;
            }

            int prev3 = nums[i];
            if (isUp) {
                if (prev3 < prev2) {
                    count++;
                    isUp = false;
                }
            } else {
                if (prev3 > prev2) {
                    count++;
                    isUp = true;
                }
            }
            prev1 = prev2;
            prev2 = prev3;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.62 MB (Beats: 26.26%)

<br>
