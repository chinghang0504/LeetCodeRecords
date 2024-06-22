# [LeetCode Records](../../README.md) - Question 3146 Permutation Difference between Two Strings

### Attempt 1: Use two int[] to save the indices of characters
```java
class Solution {
    public int findPermutationDifference(String s, String t) {
        char[] arr1 = s.toCharArray();
        char[] arr2 = t.toCharArray();
        int n = arr1.length;
        int[] counts1 = new int[26];
        int[] counts2 = new int[26];

        for (int i = 0; i < n; i++) {
            counts1[arr1[i] - 'a'] = i;
        }
        for (int i = 0; i < n; i++) {
            counts2[arr2[i] - 'a'] = i;
        }

        int sum = 0;
        for (int i = 0; i < 26; i++) {
            sum += Math.abs(counts1[i] - counts2[i]);
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 43.01 MB (Beats: 18.65%)

<br>
