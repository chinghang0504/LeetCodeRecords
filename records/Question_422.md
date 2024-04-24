# [LeetCode Records](../README.md) - Question 422 Valid Word Square

### Attempt 1: Convert a list of Strings  to a 2d array
```java
class Solution {
    public boolean validWordSquare(List<String> words) {
        int n = words.size();
        char[][] wordSquare = new char[n][n];

        int index = 0;
        for (String word : words) {
            char[] wordArray = word.toCharArray();
            if (wordArray.length > n) {
                return false;
            }

            System.arraycopy(wordArray, 0, wordSquare[index++], 0, wordArray.length);
        }

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if (wordSquare[i][j] != wordSquare[j][i]) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 42.90 MB (Beats: 27.19%)

<br>
