# [LeetCode Records](../../README.md) - Question 2955 Number of Same-End Substrings

### Attempt 1: Use an int[][] to store the cumulative character counts
```java
class Solution {
    public int[] sameEndSubstringCount(String s, int[][] queries) {
        char[] arr = s.toCharArray();
        int[][] counts = new int[arr.length + 1][26];
        for (int i = 1; i <= arr.length; i++) {
            for (int j = 0; j < 26; j++) {
                counts[i][j] = counts[i - 1][j];
            }
            counts[i][arr[i - 1] - 'a']++;
        }

        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int[] counts1 = counts[queries[i][0]];
            int[] counts2 = counts[queries[i][1] + 1];

            int count = 0;
            for (int j = 0; j < 26; j++) {
                int value = counts2[j] - counts1[j];
                count += (1 + value) * value / 2;
            }
            ans[i] = count;
        }

        return ans;
    }
}
```
- Runtime: 39 ms (Beats: 94.06%)
- Memory: 59.99 MB (Beats: 5.62%)

<br>
