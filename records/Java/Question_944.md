# [LeetCode Records](../../README.md) - Question 944 Delete Columns to Make Sorted

### Attempt 1: Convert the String[] to char[][]
```java
class Solution {
    public int minDeletionSize(String[] strs) {
        int n = strs.length;

        char[][] words = new char[n][];
        for (int i = 0; i < n; i++) {
            words[i] = strs[i].toCharArray();
        }

        int length = words[0].length;
        int deletedSize = 0;
        for (int j = 0; j < length; j++) {
            for (int i = 1; i < n; i++) {
                if (words[i - 1][j] > words[i][j]) {
                    deletedSize++;
                    break;
                }
            }
        }

        return deletedSize;
    }
}
```
- Runtime: 5 ms (Beats: 97.60%)
- Memory: 45.34 MB (Beats: 5.65%)

<br>
