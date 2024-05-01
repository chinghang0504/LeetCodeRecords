# [LeetCode Records](../../README.md) - Question 504 

### Attempt 1: Loop for calculating the remainder and the quotient
```java
class Solution {
    public String convertToBase7(int num) {
        StringBuilder stringBuilder = new StringBuilder();
        int absNum = Math.abs(num);

        while (absNum >= 7) {
            stringBuilder.append((char)((absNum % 7) + '0'));
            absNum /= 7;
        }
        stringBuilder.append((char)(absNum + '0'));

        if (num < 0) {
            stringBuilder.append('-');
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.62 MB (Beats: 88.21%)

<br>
