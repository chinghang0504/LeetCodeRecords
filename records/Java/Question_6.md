# [LeetCode Records](../../README.md) - Question 6 Zigzag Conversion

### Attempt 1: Use multiple StringBuilder
```java
class Solution {
    public String convert(String s, int numRows) {
        StringBuilder[] lists = new StringBuilder[numRows];
        for (int row = 0; row < numRows; row++) {
            lists[row] = new StringBuilder();
        }
        int factor = -1;

        for (int row = 0, ch = 0; ch < s.length(); ch++, row += factor) {
            lists[row].append(s.charAt(ch));

            if (numRows == 1) {
                factor = 0;
            } else {
                if (row == 0) {
                    factor = 1;
                } else if (row == numRows - 1) {
                    factor = -1;
                }
            }
        }

        for (int row = 1; row < numRows; row++) {
            lists[0].append(lists[row]);
        }

        return lists[0].toString();
    }
}
```
- Runtime: 4 ms (Beats: 80.67%)
- Memory: 44.42 MB (Beats: 91.09%)

<br>
