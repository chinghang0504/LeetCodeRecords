# [LeetCode Records](../../README.md) - Question 809 Expressive Words

### Attempt 1: Compare the number of the same characters on both side
```java
class Solution {
    public int expressiveWords(String s, String[] words) {
        char[] arr = s.toCharArray();

        int count = 0;
        for (String word : words) {
            if (isStretchy(arr, word.toCharArray())) {
                count++;
            }
        }

        return count;
    }

    private boolean isStretchy(char[] arr, char[] wordArr) {
        int index = 0;
        int wordIndex = 0;
        
        while (index < arr.length && wordIndex < wordArr.length) {
            if (arr[index] != wordArr[wordIndex]) {
                return false;
            }

            int i = index + 1;
            while (i < arr.length && arr[i - 1] == arr[i]) {
                i++;
            }
            int arrCount = i - index;

            int j = wordIndex + 1;
            while (j < wordArr.length && wordArr[j - 1] == wordArr[j]) {
                j++;
            }
            int wordArrCount = j - wordIndex;

            if (arrCount < wordArrCount || arrCount == 2 && wordArrCount == 1) {
                return false;
            }

            index = i;
            wordIndex = j;
        }

        return index == arr.length && wordIndex == wordArr.length;
    }
}
```
- Runtime: 1 ms (Beats: 99.67%)
- Memory: 41.53 MB (Beats: 87.26%)

<br>
