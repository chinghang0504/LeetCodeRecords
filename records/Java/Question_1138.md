# [LeetCode Records](../../README.md) - Question 1138 Alphabet Board Path

### Attempt 1: Compare the current position with the target position
```java
class Solution {
    public String alphabetBoardPath(String target) {
        StringBuilder stringBuilder = new StringBuilder();

        int currI = 0;
        int currJ = 0;
        for (char ch : target.toCharArray()) {
            int value = ch - 'a';
            int targetI = value / 5;
            int targetJ = value % 5;

            if (currI <= targetI) {
                while (currJ < targetJ) {
                    currJ++;
                    stringBuilder.append('R');
                }
                while (currJ > targetJ) {
                    currJ--;
                    stringBuilder.append('L');
                }
                while (currI < targetI) {
                    currI++;
                    stringBuilder.append('D');
                }
            } else {
                while (currI > targetI) {
                    currI--;
                    stringBuilder.append('U');
                }
                while (currJ < targetJ) {
                    currJ++;
                    stringBuilder.append('R');
                }
                while (currJ > targetJ) {
                    currJ--;
                    stringBuilder.append('L');
                }
            }

            stringBuilder.append('!');
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.20 MB (Beats: 94.44%)

<br>
