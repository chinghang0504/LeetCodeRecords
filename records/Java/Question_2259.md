# [LeetCode Records](../../README.md) - Question 2259 Remove Digit From Number to Maximize Result

### Attempt 1: Find the next character that is larger than the target digit
```java
class Solution {
    public String removeDigit(String number, char digit) {
        char[] arr = number.toCharArray();
        int targetIndex = -1;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i - 1] == digit && digit < arr[i]) {
                targetIndex = i - 1;
                break;
            }
        }

        if (targetIndex == -1) {
            for (int i = arr.length - 1; i >= 0; i--) {
                if (arr[i] == digit) {
                    targetIndex = i;
                    break;
                }
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < arr.length; i++) {
            if (i == targetIndex) {
                continue;
            } else {
                stringBuilder.append(arr[i]);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.60 MB (Beats: 70.71%)

<br>
