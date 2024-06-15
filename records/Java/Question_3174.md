# [LeetCode Records](../../README.md) - Question 3174 Clear Digits

### Attempt 1: Modify the target characters to space characters
```java
class Solution {
    public String clearDigits(String s) {
        char[] arr = s.toCharArray();

        while (true) {
            int index = -1;
            for (int i = 0; i < arr.length; i++) {
                if (arr[i] >= '0' && arr[i] <= '9') {
                    arr[i] = ' ';
                    index = i;
                    break;
                }
            }

            if (index == -1) {
                break;
            }

            for (int i = index - 1; i >= 0; i--) {
                if (arr[i] >= 'a' && arr[i] <= 'z') {
                    arr[i] = ' ';
                    break;
                }
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != ' ') {
                stringBuilder.append(arr[i]);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.45 MB (Beats: 55.70%)

<br>
