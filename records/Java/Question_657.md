# [LeetCode Records](../../README.md) - Question 657 Robot Return to Origin

### Attempt 1: 
```java
class Solution {
    public boolean judgeCircle(String moves) {
        int x = 0, y = 0;

        for (char ch : moves.toCharArray()) {
            if (ch == 'U') {
                y++;
            } else if (ch == 'D') {
                y--;
            } else if (ch == 'L') {
                x--;
            } else {
                x++;
            }
        }

        return x == 0 && y == 0;
    }
}
```
- Runtime: 4 ms (Beats: 97.65%)
- Memory: 44.16 MB (Beats: 82.91%)

<br>
