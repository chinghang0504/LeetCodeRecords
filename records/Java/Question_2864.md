# [LeetCode Records](../../README.md) - Question 2864 Maximum Odd Binary Number

### Attempt 1: Count the number of zeros and ones first
```java
class Solution {
    public String maximumOddBinaryNumber(String s) {
        int countOnes = 0;
        int countZeros = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '1') {
                countOnes++;
            } else {
                countZeros++;
            }
        }

        StringBuilder stringBuilder = new StringBuilder();

        for (int i = 0; i < countOnes - 1; i++) {
            stringBuilder.append('1');
        }
        for (int i = 0; i < countZeros; i++) {
            stringBuilder.append('0');
        }
        stringBuilder.append('1');

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 43.06 MB (Beats: 70.45%)

<br>
