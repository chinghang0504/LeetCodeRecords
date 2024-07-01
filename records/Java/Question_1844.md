# [LeetCode Records](../../README.md) - Question 1844 Replace All Digits with Characters

### Attempt 1: Use a loop
```java
class Solution {
    public String replaceDigits(String s) {
        StringBuilder stringBuilder = new StringBuilder();
        char[] arr = s.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] >= 'a' && arr[i] <= 'z') {
                stringBuilder.append(arr[i]);
            } else {
                stringBuilder.append((char)(arr[i - 1] + arr[i] - '0'));
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.10 MB (Beats: 95.30%)

<br>
