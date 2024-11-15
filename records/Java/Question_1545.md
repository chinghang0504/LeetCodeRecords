# [LeetCode Records](../../README.md) - Question 1545 Find Kth Bit in Nth Binary String

### Attempt 1: Generate all the strings
```java
class Solution {
    public char findKthBit(int n, int k) {
        String str = "0";

        for (int i = 1; i <= n; i++) {
            str = str + "1" + reverseAndInvert(str);
        }

        return str.charAt(k - 1);
    }

    private String reverseAndInvert(String str) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : str.toCharArray()) {
            if (ch == '0') {
                stringBuilder.append('1');
            } else {
                stringBuilder.append('0');
            }
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 193 ms (Beats: 5.03%)
- Memory: 56.61 MB (Beats: 5.60%)

<br>
