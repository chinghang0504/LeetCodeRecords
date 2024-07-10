# [LeetCode Records](../../README.md) - Question 2309 Greatest English Letter in Upper and Lower Case

### Attempt 1: Use two boolean[]
```java
class Solution {
    public String greatestLetter(String s) {
        boolean[] lowerCaseIndices = new boolean[26];
        boolean[] upperCaseIndices = new boolean[26];
        char[] arr = s.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            char ch = arr[i];
            if (ch >= 'a') {
                lowerCaseIndices[ch - 'a'] = true;
            } else {
                upperCaseIndices[ch - 'A'] = true;
            }
        }

        for (int i = 25; i >= 0; i--) {
            if (lowerCaseIndices[i] && upperCaseIndices[i]) {
                return String.valueOf((char)('A' + i));
            }
        }

        return "";
    }
}
```
- Runtime: 2 ms (Beats: 79.20%)
- Memory: 41.80 MB (Beats: 82.90%)

<br>
