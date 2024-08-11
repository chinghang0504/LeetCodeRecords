# [LeetCode Records](../../README.md) - Question 3248 Snake in Matrix

### Attempt 1: Use a for loop to get each command
```java
class Solution {
    public int finalPositionOfSnake(int n, List<String> commands) {
        int i = 0;
        int j = 0;

        for (String command : commands) {
            switch (command) {
                case "UP":
                    i -= 1;
                    break;
                case "DOWN":
                    i += 1;
                    break;
                case "LEFT":
                    j -= 1;
                    break;
                case "RIGHT":
                    j += 1;
                    break;
            }
        }

        return i * n + j;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.49 MB (Beats: 100.00%)

<br>
