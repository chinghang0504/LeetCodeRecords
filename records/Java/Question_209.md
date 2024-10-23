# [LeetCode Records](../../README.md) - Question 209 Minimum Size Subarray Sum

### Attempt 1: Use sliding window technique
```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int sum = 0;
        int i = 0;
        while (i < nums.length && sum < target) {
            sum += nums[i];
            i++;
        }

        if (sum < target) {
            return 0;
        }

        int minLength = i;
        int startIndex = 0;
        while (true) {
            while (sum - nums[startIndex] >= target) {
                sum -= nums[startIndex];
                minLength--;
                startIndex++;
            }

            if (i < nums.length) {
                sum = sum + nums[i] - nums[startIndex];
                startIndex++;
                i++;
            } else {
                break;
            }
        }

        return minLength;
    }
}
```
- Runtime: 1 ms (Beats: 99.57%)
- Memory: 57.74 MB (Beats: 77.63%)

<br>
