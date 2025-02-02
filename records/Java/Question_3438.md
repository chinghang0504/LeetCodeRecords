# [LeetCode Records](../../README.md) - Question 3438 Find Valid Pair of Adjacent Digits in String

### Attempt 1: Use an int[] to record the digit counts
```java
class Solution {
    public String findValidPair(String s) {
        char[] arr = s.toCharArray();

        int[] counts = new int[10];
        for (char ch : arr) {
            counts[ch - '0']++;
        }

        boolean isFisrtSameCount = counts[arr[0] - '0'] == arr[0] - '0';
        for (int i = 1; i < arr.length; i++) {
            boolean isSecondSameCount = counts[arr[i] - '0'] == arr[i] - '0';
            if (isFisrtSameCount && isSecondSameCount && arr[i - 1] != arr[i]) {
                StringBuilder stringBuilder = new StringBuilder();
                stringBuilder.append(arr[i - 1]);
                stringBuilder.append(arr[i]);
                return stringBuilder.toString();
            }

            isFisrtSameCount = isSecondSameCount;
        }

        return "";
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.56 MB (Beats: 100.00%)

<br>
