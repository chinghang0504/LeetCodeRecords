# [LeetCode Records](../../README.md) - Question 2529 Maximum Count of Positive Integer and Negative Integer

### Attempt 1: Use a loop
```java
class Solution {
    public int maximumCount(int[] nums) {
        int negCount = 0;
        int posCount = 0;

        for (int num : nums) {
            if (num > 0) {
                posCount++;
            } else if (num < 0) {
                negCount++;
            }
        }

        return Math.max(negCount, posCount);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.92 MB (Beats: 25.87%)

<br>
