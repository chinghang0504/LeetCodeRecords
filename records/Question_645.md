# [LeetCode Records](../README.md) - Question 645 Set Mismatch

### Attempt 1: Count all the numbers
```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int[] saved = new int[nums.length + 1];
        for (int num : nums) {
            saved[num]++;
        }

        int repeatedNum = 0;
        int missingNum = 0;
        for (int i = 1; i <= nums.length; i++) {
            if (saved[i] != 1) {
                if (saved[i] == 2) {
                    repeatedNum = i;
                } else {
                    missingNum = i;
                }
            }
        }

        return new int[]{repeatedNum, missingNum};
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.60 MB (Beats: 36.43%)

<br>
