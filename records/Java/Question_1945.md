# [LeetCode Records](../../README.md) - Question 1945 Sum of Digits of String After Convert

### Attempt 1: Use two loops
```java
class Solution {
    public int getLucky(String s, int k) {
        int num = 0;
        for (char ch : s.toCharArray()) {
            int val = ch - 'a' + 1;
            num += val / 10 + val % 10;
        }

        for (int i = 0; i < k - 1; i++) {
            int nextNum = 0;
            while (num > 0) {
                nextNum += num % 10;
                num /= 10;
            }
            num = nextNum;
        }

        return num;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.86 MB (Beats: 43.10%)

<br>
