# [LeetCode Records](../../README.md) - Question 844 Backspace String Compare

### Attempt 1: Use a helper function that gets the backspace string
```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        String s1 = getBackspaceString(s);
        String s2 = getBackspaceString(t);

        return s1.equals(s2);
    }

    private String getBackspaceString(String str) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : str.toCharArray()) {
            if (ch == '#') {
                int index = stringBuilder.length() - 1;
                if (index >= 0) {
                    stringBuilder.deleteCharAt(index);
                }
            } else {
                stringBuilder.append(ch);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.44 MB (Beats: 64.20%)

<br>
