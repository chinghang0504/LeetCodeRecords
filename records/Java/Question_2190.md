# [LeetCode Records](../../README.md) - Question 2190 Most Frequent Number Following Key In an Array

### Attempt 1: Use an int[] to record number counts
```java
class Solution {
    public int mostFrequent(int[] nums, int key) {
        int[] counts = new int[1001];

        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] == key) {
                counts[nums[i + 1]]++;
            }
        }

        int max = 0;
        int maxIndex = 0;
        for (int i = 1; i < 1001; i++) {
            if (counts[i] > max) {
                max = counts[i];
                maxIndex = i;
            }
        }

        return maxIndex;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.04 MB (Beats: 65.48%)

<br>
