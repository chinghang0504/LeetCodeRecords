# [LeetCode Records](../../README.md) - Question 560 Subarray Sum Equals K

### Attempt 1: Use an int[] to store the prefix sums and a HashMap to store the previous checked prefix sums
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int[] prefixSums = new int[nums.length + 1];
        for (int i = 0; i < nums.length; i++) {
            prefixSums[i + 1] = prefixSums[i] + nums[i];
        }

        Map<Integer, Integer> map = new HashMap<>();
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (prefixSums[i + 1] == k) {
                count++;
            }

            int target = prefixSums[i + 1] - k;
            Integer targetCount = map.get(target);
            if (targetCount != null) {
                count += targetCount;
            }

            map.merge(prefixSums[i + 1], 1, Integer::sum);
        }

        return count;
    }
}
```
- Runtime: 15 ms (Beats: 99.91%)
- Memory: 46.70 MB (Beats: 31.32%)

<br>
