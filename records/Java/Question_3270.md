# [LeetCode Records](../../README.md) - Question 3270 Find the Key of the Numbers

### Attempt 1: Use String.format() to get the strings with padding zeros
```java
class Solution {
    public int generateKey(int num1, int num2, int num3) {
        String str1 = String.format("%04d", num1);
        String str2 = String.format("%04d", num2);
        String str3 = String.format("%04d", num3);

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < 4; i++) {
            char ch = (char) Math.min(Math.min(str1.charAt(i), str2.charAt(i)), str3.charAt(i));
            stringBuilder.append(ch);
        }

        return Integer.valueOf(stringBuilder.toString());
    }
}
```
- Runtime: 12 ms (Beats: 100.00%)
- Memory: 42.55 MB (Beats: 100.00%)

<br>
