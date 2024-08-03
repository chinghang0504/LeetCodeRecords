# [LeetCode Records](../../README.md) - Question 997 Find the Town Judge

### Attempt 1: Use a boolean[][] to save the records
```java
class Solution {
    public int findJudge(int n, int[][] trust) {
        boolean[][] records = new boolean[n][n];

        for (int[] item : trust) {
            records[item[1] - 1][item[0] - 1] = true;
        }

        for (int i = 0; i < n; i++) {
            if (isEverybodyTrust(i, records[i]) && isTrustNobody(i, records)) {
                return i + 1;
            }
        }

        return -1;
    }

    private boolean isEverybodyTrust(int judge, boolean[] record) {
        for (int i = 0; i < record.length; i++) {
            if (i == judge) {
                continue;
            }

            if (!record[i]) {
                return false;
            }
        }

        return true;
    }

    private boolean isTrustNobody(int judge, boolean[][] records) {
        for (int i = 0; i < records.length; i++) {
            if (records[i][judge]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 60.92%)
- Memory: 53.98 MB (Beats: 29.33%)

<br>
