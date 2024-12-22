# [LeetCode Records](../../README.md) - Question 3396 Minimum Number of Operations to Make Elements in Array Distinct

### Attempt 1: Use a HashSet to store the searched numbers
```java
class Solution {
    public int minimumOperations(int[] nums) {
        Set<Integer> set = new HashSet<>();
        int i = nums.length - 1;
        for (; i >= 0 && !set.contains(nums[i]); i--) {
            set.add(nums[i]);
        }

        return i < 0 ? 0 : Math.ceilDiv(i + 1, 3);
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.34 MB (Beats: 100.00%)

<br>
