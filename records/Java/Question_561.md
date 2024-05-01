# [LeetCode Records](../../README.md) - Question 561 Array Partition

### Attempt 1: Sort the array first
```java
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);

        int count = 0;
        
        for (int i = 0; i < nums.length - 1; i += 2) {
            count += nums[i];
        }

        return count;
    }
}
```
- Runtime: 12 ms (Beats: 97.01%)
- Memory: 46.58 MB (Beats: 41.16%)

<br>
