# [LeetCode Records](../../README.md) - Question 1190 Reverse Substrings Between Each Pair of Parentheses

### Attempt 1: Keep checking the character ')'
```java
class Solution {
    public String reverseParentheses(String s) {
        List<Character> list = new LinkedList<>();

        for (char ch : s.toCharArray()) {
            if (ch == ')') {
                List<Character> wordList = new LinkedList<>();
                char lastCh = list.removeLast();
                while (lastCh != '(') {
                    wordList.add(lastCh);
                    lastCh = list.removeLast();
                }
                list.addAll(wordList);
            } else {
                list.add(ch);
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (char ch : list) {
            stringBuilder.append(ch);
        }
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 12 ms (Beats: 19.48%)
- Memory: 45.30 MB (Beats: 5.95%)

<br>
