# [LeetCode Records](../../README.md) - Question 930 Binary Subarrays With Sum

### Attempt 1: Use an int[] to store the counts of prefix sums
```java
class Solution {
    public int numSubarraysWithSum(int[] nums, int goal) {
        int ans = 0;
        int[] counts = new int[nums.length + 1];
        counts[0] = 1;

        int prefixSum = 0;        
        for (int i = 0; i < nums.length; i++) {
            prefixSum += nums[i];

            int target = prefixSum - goal;
            if (target >= 0) {
                ans += counts[target];
            }

            counts[prefixSum]++;
        }

        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 66.25%)
- Memory: 48.48 MB (Beats: 32.18%)

<br>
