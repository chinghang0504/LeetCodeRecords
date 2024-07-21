# [LeetCode Records](../../README.md) - Question 2451 Odd String Difference

### Attempt 1: Use an int[][] to save differences
```java
class Solution {
    public String oddString(String[] words) {
        int n = words[0].length();
        int[][] diffs = new int[words.length][n - 1];

        for (int i = 0; i < words.length; i++) {
            char[] arr = words[i].toCharArray();
            for (int j = 0; j < arr.length - 1; j++) {
                diffs[i][j] = arr[j + 1] - arr[j];
            }
        }

        int[] target = diffs[0];
        if (Arrays.equals(diffs[0], diffs[words.length - 1])) {
            for (int i = 1; i < words.length; i++) {
                if (!Arrays.equals(target, diffs[i])) {
                    return words[i];
                }
            }
        } else {
            if (Arrays.equals(target, diffs[1])) {
                return words[words.length - 1];
            } else {
                return words[0];
            }
        }

        return "";
    }
}
```
- Runtime: 1 ms (Beats: 85.25%)
- Memory: 41.66 MB (Beats: 35.94%)

<br>
