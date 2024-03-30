# [LeetCode Records](../README.md) - Question 

### Attempt 1: Loop from end of the string
```java
class Solution {
    public int titleToNumber(String columnTitle) {
        int columnNum = 0;
        int multiplier = 1;

        for (int i = columnTitle.length() - 1; i >= 0; i--) {
            int value = columnTitle.charAt(i) - 64;
            columnNum += value * multiplier;
            multiplier *= 26;
        }

        return columnNum;
    }
}
```
- Runtime: 1 ms (Beats: 96.61%)
- Memory: 41.97 MB (Beats: 75.85%)

<br>

### Attempt 2: Loop from start of the string
```java
class Solution {
    public int titleToNumber(String columnTitle) {
        int size = columnTitle.length();
        int columnNum = 0;

        for (int i = 0; i < size; i++) {
            columnNum *= 26;
            columnNum += columnTitle.charAt(i) - 64;
        }

        return columnNum;
    }
}
```
- Runtime: 1 ms (Beats: 96.61%)
- Memory: 42.15 MB (Beats: 44.51%)

<br>
