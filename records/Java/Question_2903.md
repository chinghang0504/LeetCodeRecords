# [LeetCode Records](../../README.md) - Question 2903 Find Indices With Index and Value Difference I

### Attempt 1: Use a nested loop to test every case
```java
class Solution {
    public int[] findIndices(int[] nums, int indexDifference, int valueDifference) {
        for (int i = 0; i < nums.length - indexDifference; i++) {
            for (int j = i + indexDifference; j < nums.length; j++) {
                if (Math.abs(nums[i] - nums[j]) >= valueDifference) {
                    return new int[]{i, j};
                }
            }
        }

        return new int[]{-1, -1};
    }
}
```
- Runtime: 1 ms (Beats: 98.88%)
- Memory: 43.55 MB (Beats: 19.33%)

<br>
