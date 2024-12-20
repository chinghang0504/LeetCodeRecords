# [LeetCode Records](../../README.md) - Question 474 Ones and Zeroes

### Attempt 1: Use an int[][][] as a cache
```java
class Solution {

    private int maxSize;
    private int[][] counts;
    private int[][][] cache;

    public int findMaxForm(String[] strs, int m, int n) {
        maxSize = 0;

        counts = new int[strs.length][2];
        for (int i = 0; i < strs.length; i++) {
            for (char ch : strs[i].toCharArray()) {
                if (ch == '0') {
                    counts[i][0]++;
                } else {
                    counts[i][1]++;
                }
            }
        }

        cache = new int[strs.length + 1][m + 1][n + 1];

        findMaxFormRecursion(0, 0, m, n);

        return maxSize;
    }

    private void findMaxFormRecursion(int currSize, int startIndex, int m, int n) {
        if (cache[startIndex][m][n] != 0 && currSize <= cache[startIndex][m][n]) {
            return;
        }
        
        cache[startIndex][m][n] = currSize;
        maxSize = Math.max(maxSize, currSize);

        for (int i = startIndex; i < counts.length; i++) {
            int nextM = m - counts[i][0];
            int nextN = n - counts[i][1];
            if (nextM >= 0 && nextN >= 0) {
                findMaxFormRecursion(currSize + 1, i + 1, nextM, nextN);
            }
        }
    }
}
```
- Runtime: 2520 ms (Beats: 5.00%)
- Memory: 74.87 MB (Beats: 39.50%)

<br>
