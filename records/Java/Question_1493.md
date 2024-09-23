# [LeetCode Records](../../README.md) - Question 1493 Longest Subarray of 1's After Deleting One Element

### Attempt 1: Use an int[][] to store the start index of 1s and its length
```java
class Solution {
    public int longestSubarray(int[] nums) {
        int[][] ones = new int[nums.length][2];
        int size = 0;

        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1) {
                count++;
            } else if (count != 0) {
                ones[size][0] = i - count;
                ones[size][1] = count;
                count = 0;
                size++;
            }
        }
        if (count != 0) {
            ones[size][0] = nums.length - count;
            ones[size][1] = count;
            count = 0;
            size++;
        }

        if (size == 0) {
            return 0;
        } else if (size == 1) {
            return ones[0][1] == nums.length ? ones[0][1] - 1 : ones[0][1];
        }

        int maxLength = ones[0][1];
        for (int i = 1; i < size; i++) {
            if (ones[i - 1][0] + ones[i - 1][1] + 1 == ones[i][0]) {
                maxLength = Math.max(maxLength, ones[i - 1][1] + ones[i][1]);
            } else {
                maxLength = Math.max(maxLength, ones[i][1]);
            }
        }

        return maxLength;
    }
}
```
- Runtime: 15 ms (Beats: 5.21%)
- Memory: 58.02 MB (Beats: 6.13%)

<br>
