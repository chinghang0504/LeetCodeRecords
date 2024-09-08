# [LeetCode Records](../../README.md) - Question 3280 Convert Date to Binary

### Attempt 1: Use Integer.toBinaryString() to convert an integer to a binary string
```java
class Solution {
    public String convertDateToBinary(String date) {
        int year = Integer.valueOf(date.substring(0, 4));
        String yearStr = Integer.toBinaryString(year);
        
        int month = Integer.valueOf(date.substring(5, 7));
        String monthStr = Integer.toBinaryString(month);

        int day = Integer.valueOf(date.substring(8, 10));
        String dayStr = Integer.toBinaryString(day);

        return String.format("%s-%s-%s", yearStr, monthStr, dayStr);
    }
}
```
- Runtime: 6 ms (Beats: 100.00%)
- Memory: 42.10 MB (Beats: 100.00%)

<br>
