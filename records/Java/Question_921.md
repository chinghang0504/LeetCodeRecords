# [LeetCode Records](../../README.md) - Question 921 Minimum Add to Make Parentheses Valid

### Attempt 1: Use a LinkedList to store the characters
```java
class Solution {
    public int minAddToMakeValid(String s) {
        List<Character> list = new LinkedList<>();
        
        for (char ch : s.toCharArray()) {
            if (ch == ')' && !list.isEmpty() && list.getLast() == '(') {
                list.removeLast();
            } else {
                list.addLast(ch);
            }
        }

        return list.size();
    }
}
```
- Runtime: 1 ms (Beats: 62.59%)
- Memory: 41.61 MB (Beats: 16.36%)

<br>
