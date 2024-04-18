# [LeetCode Records](../README.md) - Question 168 Excel Sheet Column Title

### Attempt 1: 
```java
class Solution {
    public String convertToTitle(int columnNumber) {
        StringBuilder stringBuilder = new StringBuilder();

        while (columnNumber > 0) {
            int offset = (columnNumber - 1) % 26;
            stringBuilder.append((char)(offset + 'A'));
            columnNumber = (columnNumber - 1) / 26;
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.48 MB (Beats: 79.54%)

<br>
