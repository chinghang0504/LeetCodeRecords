# [LeetCode Records](../../README.md) - Question 1128 Number of Equivalent Domino Pairs

### Attempt 1: Use an int[][] to save the dominoes and a helper function to calculate the combination
```java
class Solution {
    public int numEquivDominoPairs(int[][] dominoes) {
        int[][] counts = new int[10][10];

        for (int[] domino : dominoes) {
            counts[domino[0]][domino[1]]++;
        }

        int total = 0;
        for (int i = 1; i <= 9; i++) {
            for (int j = i + 1; j <= 9; j++) {
                total += getCombination(counts[i][j] + counts[j][i]);
            }
        }
        for (int i = 1; i <= 9; i++) {
            total += getCombination(counts[i][i]);
        }

        return total;
    }

    private int getCombination(int n) {
        return n * (n - 1) / 2;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 52.58 MB (Beats: 78.57%)

<br>
