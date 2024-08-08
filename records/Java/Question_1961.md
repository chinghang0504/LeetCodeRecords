# [LeetCode Records](../../README.md) - Question 1961 Check If String Is a Prefix of Array

### Attempt 1: Track the current index of the character
```java
class Solution {
    public boolean isPrefixString(String s, String[] words) {
        char[] arr = s.toCharArray();
        int arrIndex = 0;
        
        for (String word : words) {
            char[] wordArr = word.toCharArray();
            for (int i = 0; i < wordArr.length; i++) {
                if (arr[arrIndex] != wordArr[i]) {
                    return false;
                } else {
                    arrIndex++;

                    if (arrIndex == arr.length) {
                        return i == wordArr.length - 1;
                    }
                }
            }
        }

        return arrIndex == arr.length;
    }
}
```
- Runtime: 11 ms (Beats: 78.42%)
- Memory: 42.60 MB (Beats: 46.50%)

<br>
