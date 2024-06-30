# [LeetCode Records](../../README.md) - Question 1859 Sorting the Sentence

### Attempt 1: Use a String[] to save the word
```java
class Solution {
    public String sortSentence(String s) {
        String[] words = new String[9];

        StringBuilder stringBuilder = new StringBuilder();
        for (char ch : s.toCharArray()) {
            if (ch >= '0' && ch <= '9') {
                int index = ch - '0' - 1;
                words[index] = stringBuilder.toString();
                stringBuilder = new StringBuilder();
            } else if (ch != ' ') {
                stringBuilder.append(ch);
            }
        }
        
        stringBuilder.append(words[0]);
        for (int i = 1; i < 9 && words[i] != null; i++) {
            stringBuilder.append(' ');
            stringBuilder.append(words[i]);
        }
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.54 MB (Beats: 24.46%)

<br>
