# [LeetCode Records](../../README.md) - Question 3163 String Compression III

### Attempt 1: Compare to the previous character
```java
class Solution {
    public String compressedString(String word) {
        char[] arr = word.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();
        char currLen = '1';
        for (int i = 1; i < arr.length; i++) {
            if (arr[i - 1] == arr[i]) {
                currLen++;
                if (currLen > '9') {
                    stringBuilder.append('9');
                    stringBuilder.append(arr[i - 1]);
                    currLen = '1';
                }
            } else {
                stringBuilder.append(currLen);
                stringBuilder.append(arr[i - 1]);
                currLen = '1';
            }
        }
        stringBuilder.append(currLen);
        stringBuilder.append(arr[arr.length - 1]);

        return stringBuilder.toString();
    }
}
```
- Runtime: 14 ms (Beats: 97.95%)
- Memory: 46.13 MB (Beats: 27.41%)

<br>
