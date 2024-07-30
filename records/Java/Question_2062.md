# [LeetCode Records](../../README.md) - Question 2062 Count Vowel Substrings of a String

### Attempt 1: Use two helper functions that test every case
```java
class Solution {
    public int countVowelSubstrings(String word) {
        char[] arr = word.toCharArray();
        int count = 0;

        for (int i = 5; i <= arr.length; i++) {
            count += getVowelSubstringCount(arr, i);
        }

        return count;
    }

    private int getVowelSubstringCount(char[] arr, int n) {
        int count = 0;

        for (int i = 0; i < arr.length - n + 1; i++) {
            if (isVowelSubstring(arr, i, i + n)) {
                count++;
            }
        }

        return count;
    }

    private boolean isVowelSubstring(char[] arr, int startIndex, int endIndex) {
        boolean chA = false, chE = false, chI = false, chO = false, chU = false;

        for (int i = startIndex; i < endIndex; i++) {
            switch (arr[i]) {
                case 'a':
                    chA = true;
                    break;
                case 'e':
                    chE = true;
                    break;
                case 'i':
                    chI = true;
                    break;
                case 'o':
                    chO = true;
                    break;
                case 'u':
                    chU = true;
                    break;
                default:
                    return false;
            }
        }

        return chA && chE && chI && chO && chU;
    }
}
```
- Runtime: 17 ms (Beats: 34.04%)
- Memory: 41.24 MB (Beats: 93.62%)

<br>
