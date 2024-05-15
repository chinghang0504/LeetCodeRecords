# [LeetCode Records](../../README.md) - Question 1021 Remove Outermost Parentheses

### Attempt 1: Use an ArrayList to record characters
```java
class Solution {
    public String removeOuterParentheses(String s) {
        StringBuilder stringBuilder = new StringBuilder();
        List<Character> list = new ArrayList<>();

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                list.addLast(ch);
                if (list.size() > 1) {
                    stringBuilder.append(ch);
                }
            } else {
                if (list.size() > 1) {
                    stringBuilder.append(ch);
                }
                list.removeLast();
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 5 ms (Beats: 61.55%)
- Memory: 42.03 MB (Beats: 63.36%)

<br>

### Attempt 2: Use a int to count the number of current characters
```java
class Solution {
    public String removeOuterParentheses(String s) {
        StringBuilder stringBuilder = new StringBuilder();
        int count = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                count++;
                if (count > 1) {
                    stringBuilder.append(ch);
                }
            } else {
                if (count > 1) {
                    stringBuilder.append(ch);
                }
                count--;
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 2 ms (Beats: 99.52%)
- Memory: 41.82 MB (Beats: 84.50%)

<br>
