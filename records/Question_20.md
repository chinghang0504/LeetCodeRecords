# [LeetCode Records](../README.md) - Question 20 Valid Parentheses

### Attempt 1: Use ArrayList
```java
class Solution {
    public boolean isValid(String s) {
        ArrayList<Character> list = new ArrayList<>();

        for (int i = 0; i < s.length(); i++) {
            char ch1 = s.charAt(i);
            if (ch1 == '(' || ch1 == '{' || ch1 == '[') {
                list.add(ch1);
            } else {
                if (list.size() == 0) {
                    return false;
                }
                
                char ch2 = list.removeLast();
                if (ch2 == '(' && ch1 != ')') {
                    return false;
                } else if (ch2 == '{' && ch1 != '}') {
                    return false;
                } else if (ch2 == '[' && ch1 != ']') {
                    return false;
                }
            }
        }

        return list.size() == 0;
    }
}
```
- Runtime: 1 ms (Beats: 98.66%)
- Memory: 41.66 MB (Beats: 19.44%)

<br>
