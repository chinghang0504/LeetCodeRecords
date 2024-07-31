# [LeetCode Records](../../README.md) - Question 1763 Longest Nice Substring

### Attempt 1: Use a helper function that checks if it is a nice substring
```java
class Solution {
    public String longestNiceSubstring(String s) {
        char[] arr = s.toCharArray();

        for (int i = arr.length; i >= 1; i--) {
            for (int j = 0; j < arr.length - i + 1; j++) {
                if (isNiceSubstring(arr, j, j + i)) {
                    return s.substring(j, j + i);
                }
            }
        }

        return "";
    }

    private boolean isNiceSubstring(char[] arr, int start, int end) {
        boolean[] lowerCases = new boolean[26];
        boolean[] upperCases = new boolean[26];

        for (int i = start; i < end; i++) {
            char ch = arr[i];
            if (ch >= 'a' && ch <= 'z') {
                lowerCases[ch - 'a'] = true;
            } else {
                upperCases[ch - 'A'] = true;
            }
        }

        for (int i = 0; i < 26; i++) {
            if (lowerCases[i] != upperCases[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 9 ms (Beats: 40.90%)
- Memory: 44.71 MB (Beats: 29.39%)

<br>
