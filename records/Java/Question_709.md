# [LeetCode Records](../../README.md) - Question 709 To Lower Case

### Attempt 1: 
```java
class Solution {
    public String toLowerCase(String s) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : s.toCharArray()) {
            if (ch >= 'A' && ch <= 'Z') {
                ch += 32;
            }
            stringBuilder.append(ch);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.51 MB (Beats: 36.73%)

<br>
