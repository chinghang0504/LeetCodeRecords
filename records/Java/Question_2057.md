# [LeetCode Records](../../README.md) - Question 2057 Smallest Index With Equal Value

### Attempt 1: Use a loop
```java
class Solution {
    public int smallestEqual(int[] nums) {
        for (int i = 0; i < nums.length; i++) {
            if (i % 10 == nums[i]) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.62 MB (Beats: 98.89%)

<br>
