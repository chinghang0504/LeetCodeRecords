# [LeetCode Records](../../README.md) - Question 1680 Concatenation of Consecutive Binary Numbers

### Attempt 1: Use toBinaryString() to get the size of the integer
```java
class Solution {
    public int concatenatedBinary(int n) {
        long val = 0;

        for (int i = 1; i <= n; i++) {
            String str = Integer.toBinaryString(i);
            val = ((val << str.length()) + i) % 1_000_000_007;
        }

        return (int)val;
    }
}
```
- Runtime: 154 ms (Beats: 29.27%)
- Memory: 44.67 MB (Beats: 10.98%)

<br>

### Attempt 2: Use & operation to compare with the previous number
```java
class Solution {
    public int concatenatedBinary(int n) {
        long val = 0;

        for (int i = 1, size = 0; i <= n; i++) {
            if ((i & (i - 1)) == 0) {
                size++;
            }

            val = ((val << size) | i) % 1_000_000_007;
        }

        return (int)val;
    }
}
```
- Runtime: 24 ms (Beats: 100.00%)
- Memory: 40.80 MB (Beats: 60.98%)

<br>
