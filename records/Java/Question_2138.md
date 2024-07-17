# [LeetCode Records](../../README.md) - Question 2138 Divide a String Into Groups of Size k

### Attempt 1: Check the string is divisible
```java
class Solution {
    public String[] divideString(String s, int k, char fill) {
        int length = s.length();
        int size = length / k;
        int remainder = length % k;
        boolean isDivisible = remainder == 0;
        String[] answer = new String[isDivisible ? size : size + 1];

        int i = 0;
        for (; i < size; i++) {
            answer[i] = s.substring(i * k, (i + 1) * k);
        }

        if (!isDivisible) {
            StringBuilder stringBuilder = new StringBuilder();

            for (int j = i * k; j < length; j++) {
                stringBuilder.append(s.charAt(j));
            }

            int step = k - remainder;
            for (int j = 0; j < step; j++) {
                stringBuilder.append(fill);
            }

            answer[size] = stringBuilder.toString();
        }

        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 92.88%)
- Memory: 42.10 MB (Beats: 61.81%)

<br>
