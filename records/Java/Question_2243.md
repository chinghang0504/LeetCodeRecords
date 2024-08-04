# [LeetCode Records](../../README.md) - Question 2243 Calculate Digit Sum of a String

### Attempt 1: Use a while loop until get the result
```java
class Solution {
    public String digitSum(String s, int k) {
        while (s.length() > k) {
            StringBuilder stringBuilder = new StringBuilder();
            char[] arr = s.toCharArray();

            for (int i = 0; i < arr.length; i += k) {
                int sum = 0;
                for (int j = 0; i + j < arr.length && j < k; j++) {
                    sum += arr[i + j] - '0';
                }
                stringBuilder.append(String.valueOf(sum));
            }

            s = stringBuilder.toString();
        }

        return s;
    }
}
```
- Runtime: 1 ms (Beats: 91.75%)
- Memory: 41.66 MB (Beats: 50.97%)

<br>
