# [LeetCode Records](../../README.md) - Question 1796 Second Largest Digit in a String

### Attempt 1: Use a boolean[]
```java
class Solution {
    public int secondHighest(String s) {
        boolean[] digits = new boolean[10];

        for (char ch : s.toCharArray()) {
            int value = ch - '0';
            if (value >= 0 && value <= 9) {
                digits[value] = true;
            }
        }

        int targetIndex = -1;
        for (int i = 9; i >= 0; i--) {
            if (digits[i]) {
                targetIndex = i;
                break;
            }
        }
        for (int i = targetIndex - 1; i >= 0; i--) {
            if (digits[i]) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 97.79%)
- Memory: 41.78 MB (Beats: 83.91%)

<br>
