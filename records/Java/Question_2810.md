# [LeetCode Records](../../README.md) - Question 2810 Faulty Keyboard

### Attempt 1: Use reverse() and toCharArray()
```java
class Solution {
    public String finalString(String s) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : s.toCharArray()) {
            if (ch == 'i') {
                stringBuilder = stringBuilder.reverse();
            } else {
                stringBuilder.append(ch);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 3 ms (Beats: 98.78%)
- Memory: 44.52 MB (Beats: 71.15%)

<br>
