# [LeetCode Records](../../README.md) - Question 1657 Determine if Two Strings Are Close

### Attempt 1: Compare the numbers of the same characters
```java
class Solution {
    public boolean closeStrings(String word1, String word2) {
        char[] arr1 = word1.toCharArray();
        char[] arr2 = word2.toCharArray();
        if (arr1.length != arr2.length) {
            return false;
        }

        int[] counts1 = new int[26];
        int[] counts2 = new int[26];
        for (char ch : arr1) {
            counts1[ch - 'a']++;
        }
        for (char ch : arr2) {
            counts2[ch - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            if (counts1[i] != 0 && counts2[i] == 0 || counts1[i] == 0 && counts2[i] != 0) {
                return false;
            }
        }

        Arrays.sort(counts1);
        Arrays.sort(counts2);

        for (int i = 0; i < 26; i++) {
            if (counts1[i] != counts2[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 10 ms (Beats: 84.44%)
- Memory: 45.16 MB (Beats: 96.44%)

<br>
