# [LeetCode Records](../README.md) - Question 408 Valid Word Abbreviation

### Attempt 1: 
```java
class Solution {
    public boolean validWordAbbreviation(String word, String abbr) {
        char[] wordArr = word.toCharArray();
        char[] abbrArr = abbr.toCharArray();

        int wordIndex = 0;
        int abbrIndex = 0;

        while (wordIndex < wordArr.length && abbrIndex < abbrArr.length) {
            char ch = abbrArr[abbrIndex];

            if (Character.isAlphabetic(ch)) {
                if (wordArr[wordIndex] != abbrArr[abbrIndex]) {
                    return false;
                } else {
                    wordIndex++;
                    abbrIndex++;
                }
            } else if (ch == '0') {
                return false;
            } else {
                int value = 0;
                while (Character.isDigit(ch)) {
                    value *= 10;
                    value += ch - '0';
                    abbrIndex++;
                    if (abbrIndex >= abbrArr.length) {
                        break;
                    }
                    ch = abbrArr[abbrIndex];
                }
                wordIndex += value;
            }
        }

        return wordIndex == wordArr.length && abbrIndex == abbrArr.length;
    }
}
```
- Runtime: 1 ms (Beats: 95.85%)
- Memory: 41.90 MB (Beats: 26.84%)

<br>
