# [LeetCode Records](../../README.md) - Question 405 Convert a Number to Hexadecimal

### Attempt 1: Get the last four binary digits first
```java
class Solution {
    private final char[] hexSymbols = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f' };
    
    public String toHex(int num) {
        if (num == 0) {
            return "0";
        }

        StringBuilder stringBuilder = new StringBuilder(8);
        while (num != 0) {
            stringBuilder.append(hexSymbols[num & 0xf]);
            num >>>= 4;
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.86 MB (Beats: 50.99%)

<br>
