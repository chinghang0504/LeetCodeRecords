# [LeetCode Records](../README.md) - Question 164 Maximum Gap

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int maximumGap(int[] nums) {
        Arrays.sort(nums);

        int max = 0;
        int start = nums[0];
        for (int i = 1; i < nums.length; i++) {
            int end = nums[i];
            max = Math.max(max, end - start);
            start = end;
        }

        return max;
    }
}
```
- Runtime: 41 ms (Beats: 42.51%)
- Memory: 60.70 MB (Beats: 50.13%)

<br>
