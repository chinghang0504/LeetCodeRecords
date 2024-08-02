# [LeetCode Records](../../README.md) - Question 1592 Rearrange Spaces Between Words

### Attempt 1: Use a helper function that calculates the word and space counts
```java
class Solution {
    public String reorderSpaces(String text) {
        char[] arr = text.toCharArray();
        int[] counts = getCounts(arr);
        int wordCountMinusOne = counts[0] - 1;
        int numOfSpaces = wordCountMinusOne == 0 ? 0 : counts[1] / wordCountMinusOne;
        int extraSpaces = counts[1] - (numOfSpaces * wordCountMinusOne);
        StringBuilder stringBuilder = new StringBuilder();

        int i = 0;
        for (int wordIndex = 0; wordIndex < counts[0] - 1; wordIndex++) {
            while (arr[i] == ' ') {
                i++;
            }
            while (arr[i] != ' ') {
                stringBuilder.append(arr[i]);
                i++;
            }

            for (int j = 0; j < numOfSpaces; j++) {
                stringBuilder.append(' ');
            }
        }
        while (arr[i] == ' ') {
            i++;
        }
        while (i < arr.length && arr[i] != ' ') {
            stringBuilder.append(arr[i]);
            i++;
        }
        for (int j = 0; j < extraSpaces; j++) {
            stringBuilder.append(' ');
        }

        return stringBuilder.toString();
    }

    private int[] getCounts(char[] arr) {
        int wordCount = 0;
        int spaceCount = 0;
        boolean isWord = false;

        for (char ch : arr) {
            if (ch == ' ') {
                isWord = false;
                spaceCount++;
            } else if (!isWord) {
                isWord = true;
                wordCount++;
            }
        }

        return new int[] { wordCount, spaceCount };
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.46 MB (Beats: 69.51%)

<br>
