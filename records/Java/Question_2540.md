# [LeetCode Records](../../README.md) - Question 2540 Minimum Common Value

### Attempt 1: Use a HashSet
```java
class Solution {
    public int getCommon(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();
        
        for (int num : nums1) {
            set.add(num);
        }

        int common = Integer.MAX_VALUE;

        for (int num : nums2) {
            if (set.contains(num)) {
                common = Math.min(common, num);
            }
        }

        return common == Integer.MAX_VALUE ? -1 : common;
    }
}
```
- Runtime: 14 ms (Beats: 21.29%)
- Memory: 65.06 MB (Beats: 5.32%)

<br>
