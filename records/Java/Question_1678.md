# [LeetCode Records](../../README.md) - Question 1678 Goal Parser Interpretation

### Attempt 1: Check the first character
```java
class Solution {
    public String interpret(String command) {
        char[] arr = command.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();

        for (int i = 0; i < arr.length;) {
            if (arr[i] == 'G') {
                stringBuilder.append('G');
                i++;
            } else if (arr[i] == '(' && arr[i + 1] == ')') {
                stringBuilder.append('o');
                i += 2;
            } else {
                stringBuilder.append("al");
                i += 4;
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.40 MB (Beats: 50.03%)

<br>
