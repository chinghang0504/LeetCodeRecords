# [LeetCode Records](../../README.md) - Question 557 Reverse Words in a String III

### Attempt 1: Reverse every word
```java
class Solution {
    public String reverseWords(String s) {
        char[] words = s.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();
        
        int start = 0;
        int end = 0;

        for (int i = 0; i < words.length; i++) {
            if (words[i] == ' ') {
                reverseWord(words, start, end, stringBuilder);
                stringBuilder.append(' ');
                start = i + 1;
            } else {
                end = i;
            }
        }
        reverseWord(words, start, end, stringBuilder);

        return stringBuilder.toString();
    }

    private void reverseWord(char[] word, int start, int end, StringBuilder stringBuilder) {
        for (int i = end; i >= start; i--) {
            stringBuilder.append(word[i]);
        }
    }
}
```
- Runtime: 5 ms (Beats: 68.12%)
- Memory: 45.49 MB (Beats: 22.21%)

<br>
