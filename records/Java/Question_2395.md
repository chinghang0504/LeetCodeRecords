# [LeetCode Records](../../README.md) - Question 2395 Find Subarrays With Equal Sum

### Attempt 1: Use a HashSet to record the sum
```java
class Solution {
    public boolean findSubarrays(int[] nums) {
        Set<Integer> set = new HashSet<>();

        for (int i = 0; i < nums.length - 1; i++) {
            int sum = nums[i] + nums[i + 1];
            if (set.contains(sum)) {
                return true;
            } else {
                set.add(sum);
            }
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 99.21%)
- Memory: 42.08 MB (Beats: 5.89%)

<br>
