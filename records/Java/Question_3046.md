# [LeetCode Records](../../README.md) - Question 3046 Split the Array

### Attempt 1: Use an int[] to  record number counts
```java
class Solution {
    public boolean isPossibleToSplit(int[] nums) {
        int[] counts = new int[101];

        for (int num : nums) {
            counts[num]++;
        }

        int count2 = 0;
        for (int i = 1; i < 101; i++) {
            if (counts[i] > 2) {
                return false;
            } else if (counts[i] == 2) {
                count2++;
            }
        }

        return count2 <= nums.length / 2;
    }
}
```
- Runtime: 1 ms (Beats: 96.04%)
- Memory: 42.68 MB (Beats: 55.73%)

<br>
