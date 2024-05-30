# [LeetCode Records](../../README.md) - Question 1512 Number of Good Pairs

### Attempt 1: Use two loopss
```java
class Solution {
    public int numIdenticalPairs(int[] nums) {
        int count = 0;
        
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] == nums[j]) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 87.50%)
- Memory: 41.08 MB (Beats: 28.96%)

<br>
