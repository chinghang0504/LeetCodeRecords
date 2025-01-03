# [LeetCode Records](../../README.md) - Question 325 Maximum Size Subarray Sum Equals k

### Attempt 1: Use an int[] to store the cumulative sums
```java
class Solution {
    public int maxSubArrayLen(int[] nums, int k) {
        int[] cumulativeSums = new int[nums.length + 1];
        for (int i = 0; i < nums.length; i++) {
            cumulativeSums[i + 1] = cumulativeSums[i] + nums[i];
        }

        Map<Integer, Integer> numToMinIndexMap = new HashMap<>();
        for (int i = 0; i < cumulativeSums.length; i++) {
            if (!numToMinIndexMap.containsKey(cumulativeSums[i])) {
                numToMinIndexMap.put(cumulativeSums[i], i);
            }
        }

        int maxLen = 0;
        for (int i = cumulativeSums.length - 1; i >= 0; i--) {
            int target = cumulativeSums[i] - k;
            Integer minIndex = numToMinIndexMap.get(target);
            if (minIndex != null) {
                maxLen = Math.max(maxLen, i - minIndex);
            }
        }

        return maxLen;
    }
}
```
- Runtime: 109 ms (Beats: 30.31%)
- Memory: 71.11 MB (Beats: 93.45%)

<br>
