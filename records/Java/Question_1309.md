# [LeetCode Records](../../README.md) - Question 1309 Decrypt String from Alphabet to Integer Mapping

### Attempt 1: Start from end of the string
```java
class Solution {
    public String freqAlphabets(String s) {
        char[] arr = s.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();

        for (int i = arr.length - 1; i >= 0;) {
            if (arr[i] != '#') {
                char ch = (char)(arr[i] + 48);
                stringBuilder.append(ch);
                i--;
            } else {
                char ch = (char)(arr[i - 2] == '1' ? arr[i - 1] + 58 : arr[i - 1] + 68);
                stringBuilder.append(ch);
                i -= 3;
            }
        }
        
        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.41 MB (Beats: 64.36%)

<br>
