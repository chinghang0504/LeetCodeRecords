# [LeetCode Records](../../README.md) - Question 3028 Ant on the Boundary

### Attempt 1: Use a loop
```java
class Solution {
    public int returnToBoundaryCount(int[] nums) {
        int curr = 0;
        int count = 0;

        for (int num : nums) {
            curr += num;

            if (curr == 0) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.26 MB (Beats: 19.40%)

<br>
