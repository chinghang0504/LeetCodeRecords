# [LeetCode Records](../../README.md) - Question 2873 Maximum Value of an Ordered Triplet I

### Attempt 1: Use a nested loop to test every case
```java
class Solution {
    public long maximumTripletValue(int[] nums) {
        long max = 0;

        for (int i = 0; i < nums.length - 2; i++) {
            for (int j = i + 1; j < nums.length - 1; j++) {
                long diff = nums[i] - nums[j];
                for (int k = j + 1; k < nums.length; k++) {
                    if (nums[i] < 0 && nums[j] < 0 && nums[k] < 0) {
                        continue;
                    }

                    long value = diff * nums[k];
                    max = Math.max(max, value);
                }
            }
        }

        return max;
    }
}
```
- Runtime: 3 ms (Beats: 52.42%)
- Memory: 41.61 MB (Beats: 78.49%)

<br>
