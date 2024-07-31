# [LeetCode Records](../../README.md) - Question 2784 Check if Array is Good

### Attempt 1: Use an int[] to save the number counts
```java
class Solution {
    public boolean isGood(int[] nums) {
        int[] counts = new int[nums.length];

        for (int num : nums) {
            if (num >= nums.length) {
                return false;
            } else {
                counts[num]++;
            }
        }

        for (int i = 1; i < nums.length - 1; i++) {
            if (counts[i] != 1) {
                return false;
            }
        }

        return counts[nums.length - 1] == 2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.26 MB (Beats: 17.15%)

<br>
