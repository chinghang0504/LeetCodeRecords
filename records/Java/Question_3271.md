# [LeetCode Records](../../README.md) - Question 3271 Hash Divided String

### Attempt 1: Use a nested loop to calculate the sum of characters for each substring
```java
class Solution {
    public String stringHash(String s, int k) {
        char[] arr = s.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();

        for (int i = 0; i < arr.length; i += k) {
            int sum = 0;

            for (int j = 0; j < k; j++) {
                sum += arr[i + j] - 'a';
            }
            
            stringBuilder.append((char)(sum % 26 + 'a'));
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 2 ms (Beats: 96.31%)
- Memory: 44.34 MB (Beats: 98.52%)

<br>
