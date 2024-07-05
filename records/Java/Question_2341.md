# [LeetCode Records](../../README.md) - Question 2341 Maximum Number of Pairs in Array

### Attempt 1: Use an int[] to record number counts
```java
class Solution {
    public int[] numberOfPairs(int[] nums) {
        int[] counts = new int[101];

        for (int num : nums) {
            counts[num]++;
        }

        int pairCount = 0;
        for (int count : counts) {
            pairCount += count / 2;
        }
        int remainingCount = nums.length - pairCount * 2;

        return new int[]{pairCount, remainingCount};
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.87 MB (Beats: 54.05%)

<br>
