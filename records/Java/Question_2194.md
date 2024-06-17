# [LeetCode Records](../../README.md) - Question 2194 Cells in a Range on an Excel Sheet

### Attempt 1: Use a nested loop
```java
class Solution {
    public List<String> cellsInRange(String s) {
        char[] arr = s.toCharArray();
        char col1 = arr[0];
        char row1 = arr[1];
        char col2 = arr[3];
        char row2 = arr[4];

        List<String> list = new ArrayList<>();
        for (char col = col1; col <= col2; col++) {
            for (char row = row1; row <= row2; row++) {
                list.add(String.format("%c%c", col, row));
            }
        }

        return list;
    }
}
```
- Runtime: 5 ms (Beats: 68.69%)
- Memory: 45.66 MB (Beats: 9.19%)

<br>
