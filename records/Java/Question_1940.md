# [LeetCode Records](../../README.md) - Question 1940 Longest Common Subsequence Between Sorted Arrays

### Attempt 1: Use an int[] to store the current searching index of each array
```java
class Solution {
    public List<Integer> longestCommonSubsequence(int[][] arrays) {
        int[] leftIndices = new int[arrays.length];
        List<Integer> ans = new ArrayList<>();

        for (int num : arrays[0]) {
            boolean allFound = true;
            for (int i = 1; i < arrays.length; i++) {
                while (leftIndices[i] < arrays[i].length && arrays[i][leftIndices[i]] < num) {
                    leftIndices[i]++;
                }
                if (leftIndices[i] >= arrays[i].length || arrays[i][leftIndices[i]] != num) {
                    allFound = false;
                    break;
                }
            }

            if (allFound) {
                ans.add(num);
            }
        }

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 94.00%)
- Memory: 45.32 MB (Beats: 88.00%)

<br>
