# [LeetCode Records](../../README.md) - Question 974 Subarray Sums Divisible by K

### Attempt 1: Use an int[] to store the remainder counts
```java
class Solution {
    public int subarraysDivByK(int[] nums, int k) {
        int[] remainderCounts = new int[k];
        int count = 0;

        for (int i = 0, prefixSum = 0; i < nums.length; i++) {
            prefixSum = ((prefixSum + nums[i]) % k + k) % k;
            if (prefixSum != 0) {
                count += remainderCounts[prefixSum];
                remainderCounts[prefixSum]++;
            } else {
                remainderCounts[prefixSum]++;
                count += remainderCounts[prefixSum];
            }
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 91.04%)
- Memory: 45.74 MB (Beats: 94.93%)

<br>
