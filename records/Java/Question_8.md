# [LeetCode Records](../../README.md) - Question 8 String to Integer (atoi)

### Attempt 1: Use the previous sum to check overflow
```java
class Solution {
    int value;
    boolean started;
    int factor;
    int prevValue;

    public int myAtoi(String s) {
        value = 0;
        prevValue = 0;
        started = false;
        factor = 1;

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            if (!started) {
                if (ch == ' ') {
                    continue;   
                } else {
                    started = true;
                }

                if (ch == '-') {
                    factor = -1;
                } else if (ch == '+') {
                    factor = 1;
                } else if (!processNext(ch)) {
                    return value;
                }
            } else if (!processNext(ch)) {
                return value;
            }
        }

        return value;
    }

    private boolean processNext(char ch) {
        if (!Character.isDigit(ch)) {
            return false;
        } else if (value == 0 && ch == '0') {
            return true;
        }

        value *= 10;
        value += Character.getNumericValue(ch) * factor;
        if (value / 10 != prevValue) {
            value = prevValue >= 0 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            return false;
        } else {
            prevValue = value;
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.22 MB (Beats: 64.69%)

<br>
