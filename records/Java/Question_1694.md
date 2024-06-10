# [LeetCode Records](../../README.md) - Question 1694 Reformat Phone Number

### Attempt 1: Use a char[] to save the digits
```java
class Solution {
    public String reformatNumber(String number) {
        char[] digits = new char[100];
        int size = 0;

        for (char ch : number.toCharArray()) {
            if (ch >= '0' && ch <= '9') {
                digits[size] = ch;
                size++;
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        int i = 0;
        while (size - i > 4) {
            stringBuilder.append(digits[i]);
            stringBuilder.append(digits[i + 1]);
            stringBuilder.append(digits[i + 2]);
            stringBuilder.append('-');
            i += 3;
        }

        stringBuilder.append(digits[i]);
        stringBuilder.append(digits[i + 1]);
        if (size - i == 3) {
            stringBuilder.append(digits[i + 2]);
        } else if (size - i == 4) {
            stringBuilder.append('-');
            stringBuilder.append(digits[i + 2]);
            stringBuilder.append(digits[i + 3]);
        }
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.61 MB (Beats: 64.73%)

<br>
