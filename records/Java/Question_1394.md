# [LeetCode Records](../../README.md) - Question 1394 Find Lucky Integer in an Array

### Attempt 1: Use an int[] to save the frequencies of numbers
```java
class Solution {
    public int findLucky(int[] arr) {
        int[] nums = new int[501];

        for (int num : arr) {
            nums[num]++;
        }

        for (int i = 500; i >= 1; i--) {
            if (nums[i] == i) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.92 MB (Beats: 78.34%)

<br>
