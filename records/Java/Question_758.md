# [LeetCode Records](../../README.md) - Question 758 Bold Words in String

### Attempt 1: Use a boolean[] to track which characters are bold
```java
class Solution {
    public String boldWords(String[] words, String s) {
        char[] arr = s.toCharArray();
        boolean[] boldArr = new boolean[arr.length];

        for (String word : words) {
            char[] wordArr = word.toCharArray();

            for (int i = 0; i < arr.length - wordArr.length + 1; i++) {
                if (isSubstring(arr, wordArr, i)) {
                    for (int j = 0; j < wordArr.length; j++) {
                        boldArr[i + j] = true;
                    }
                }
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        boolean isBold = false;
        for (int i = 0; i < arr.length; i++) {
            if (isBold) {
                if (!boldArr[i]) {
                    isBold = false;
                    stringBuilder.append("</b>");
                }
            } else {
                if (boldArr[i]) {
                    isBold = true;
                    stringBuilder.append("<b>");
                }
            }

            stringBuilder.append(arr[i]);
        }
        if (isBold) {
            stringBuilder.append("</b>");
        }

        return stringBuilder.toString();
    }

    private boolean isSubstring(char[] arr, char[] wordArr, int start) {
        for (int i = 0; i < wordArr.length; i++) {
            if (arr[start + i] != wordArr[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 5 ms (Beats: 92.31%)
- Memory: 42.14 MB (Beats: 44.44%)

<br>
