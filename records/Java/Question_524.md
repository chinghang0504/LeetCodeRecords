# [LeetCode Records](../../README.md) - Question 524 Longest Word in Dictionary through Deleting

### Attempt 1: Use two pointers to compare two strings at the same time
```java
class Solution {
    public String findLongestWord(String s, List<String> dictionary) {
        dictionary.sort((word1, word2) -> {
            int size1 = word1.length();
            int size2 = word2.length();
            return size1 != size2 ? size2 - size1 : word1.compareTo(word2);
        });

        char[] arr1 = s.toCharArray();
        for (String word : dictionary) {
            if (isValid(arr1, word)) {
                return word;
            }
        }

        return "";
    }

    private boolean isValid(char[] arr1, String word) {
        char[] arr2 = word.toCharArray();

        int leftIndex = 0;
        int rightIndex = 0;
        while (leftIndex < arr1.length && rightIndex < arr2.length) {
            if (arr1[leftIndex] == arr2[rightIndex]) {
                leftIndex++;
                rightIndex++;
            } else {
                leftIndex++;
            }
        }

        return rightIndex == arr2.length;
    }
}
```
- Runtime: 11 ms (Beats: 94.38%)
- Memory: 46.03 MB (Beats: 10.75%)

<br>
