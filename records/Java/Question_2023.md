# [LeetCode Records](../../README.md) - Question 2023 Number of Pairs of Strings With Concatenation Equal to Target

### Attempt 1: Test every case
```java
class Solution {
    public int numOfPairs(String[] nums, String target) {
        int count = 0;
        
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums.length; j++) {
                if (i != j && target.equals(nums[i] + nums[j])) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 26 ms (Beats: 60.91%)
- Memory: 45.04 MB (Beats: 39.21%)

<br>
