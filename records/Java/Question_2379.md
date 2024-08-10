# [LeetCode Records](../../README.md) - Question 2379 Minimum Recolors to Get K Consecutive Black Blocks

### Attempt 1: Use a helper function to count the number of white houses in the subarray
```java
class Solution {
    public int minimumRecolors(String blocks, int k) {
        char[] arr = blocks.toCharArray();
        int min = Integer.MAX_VALUE;

        for (int i = 0; i < arr.length - k + 1; i++) {
            min = Math.min(min, getWhiteCount(arr, i, k));
        }

        return min;
    }

    private int getWhiteCount(char[] arr, int start, int k) {
        int count = 0;

        for (int i = 0; i < k; i++) {
            if (arr[start + i] == 'W') {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 88.27%)
- Memory: 41.60 MB (Beats: 21.87%)

<br>
