# [LeetCode Records](../../README.md) - Question 3210 Find the Encrypted String

### Attempt 1: Use two loops
```java
class Solution {
    public String getEncryptedString(String s, int k) {
        StringBuilder stringBuilder = new StringBuilder();
        char[] arr = s.toCharArray();

        int n = k % arr.length;

        for (int i = n; i < arr.length; i++) {
            stringBuilder.append(arr[i]);
        }
        for (int i = 0; i < n; i++) {
            stringBuilder.append(arr[i]);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.49 MB (Beats: 82.82%)

<br>
