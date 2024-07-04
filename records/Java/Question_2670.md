# [LeetCode Records](../../README.md) - Question 2670 Find the Distinct Difference Array

### Attempt 1: Use two HashSet
```java
class Solution {
    public int[] distinctDifferenceArray(int[] nums) {
        int[] diff = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            Set<Integer> leftSet = new HashSet<>();
            Set<Integer> rightSet = new HashSet<>();

            for (int j = i; j >= 0; j--) {
                leftSet.add(nums[j]);
            }
            for (int j = i + 1; j < nums.length; j++) {
                rightSet.add(nums[j]);
            }
            
            diff[i] = leftSet.size() - rightSet.size();
        }

        return diff;
    }
}
```
- Runtime: 15 ms (Beats: 17.87%)
- Memory: 45.34 MB (Beats: 55.92%)

<br>
