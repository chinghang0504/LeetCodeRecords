# [LeetCode Records](../../README.md) - Question 2264 Largest 3-Same-Digit Number in String

### Attempt 1: Use a loop to find the maximum number
```java
class Solution {
    public String largestGoodInteger(String num) {
        int max = -1;
        char[] arr = num.toCharArray();

        for (int i = 0; i < arr.length - 2; i++) {
            if (arr[i] == arr[i + 1] && arr[i] == arr[i + 2]) {
                max = Math.max(max, (arr[i] - '0'));
            }
        }

        if (max != -1) {
            StringBuilder stringBuilder = new StringBuilder();
            for (int i = 0; i < 3; i++) {
                stringBuilder.append(max);
            }
            return stringBuilder.toString();
        }

        return "";
    }
}
```
- Runtime: 1 ms (Beats: 89.25%)
- Memory: 41.94 MB (Beats: 54.25%)

<br>
