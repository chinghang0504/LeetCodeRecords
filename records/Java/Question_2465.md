# [LeetCode Records](../../README.md) - Question 2465 Number of Distinct Averages

### Attempt 1: Use a HashSet
```java
class Solution {
    public int distinctAverages(int[] nums) {
        Set<Integer> set = new HashSet<>();
        int n = nums.length / 2;

        Arrays.sort(nums);

        for (int i = 0; i < n; i++) {
            int sum = nums[i] + nums[nums.length - 1 - i];
            set.add(sum);
        }

        return set.size();
    }
}
```
- Runtime: 1 ms (Beats: 98.53%)
- Memory: 41.28 MB (Beats: 18.74%)

<br>
