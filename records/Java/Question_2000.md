# [LeetCode Records](../../README.md) - Question 2000 Reverse Prefix of Word

### Attempt 1: Find the index of target character first
```java
class Solution {
    public String reversePrefix(String word, char ch) {
        char[] arr = word.toCharArray();
        int index = -1;
        
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == ch) {
                index = i;
                break;
            }
        }
        
        if (index == -1) {
            return word;
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = index; i >= 0; i--) {
            stringBuilder.append(arr[i]);
        }
        for (int i = index + 1; i < arr.length; i++) {
            stringBuilder.append(arr[i]);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.70 MB (Beats: 36.16%)

<br>
