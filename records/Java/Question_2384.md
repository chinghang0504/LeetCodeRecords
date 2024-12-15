# [LeetCode Records](../../README.md) - Question 2384 Largest Palindromic Number

### Attempt 1: Use an int[] to store the character counts
```java
class Solution {
    public String largestPalindromic(String num) {
        int[] counts = new int[10];
        for (char ch : num.toCharArray()) {
            counts[ch - '0']++;
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 9; i >= 1; i--) {
            if (counts[i] / 2 > 0) {
                counts[i] -= 2;
                stringBuilder.append((char)(i + '0'));
                break;
            }
        }

        if (stringBuilder.length() > 0) {
            for (int i = 9; i >= 0; i--) {
                int time = counts[i] / 2;
                counts[i] -= time * 2;

                for (int j = 0; j < time; j++) {
                    stringBuilder.append((char)(i + '0'));
                }
            }
        }

        String firstPart = stringBuilder.toString();
        String secondPart = stringBuilder.reverse().toString();
        for (int i = 9; i >= 0; i--) {
            if (counts[i] > 0) {
                return firstPart + (char)(i + '0') + secondPart;
            }
        }

        return firstPart + secondPart;
    }
}
```
- Runtime: 14 ms (Beats: 73.09%)
- Memory: 45.70 MB (Beats: 35.21%)

<br>
