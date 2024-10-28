# [LeetCode Records](../../README.md) - Question 371 Sum of Two Integers

### Attempt 1: Use the concept of full adder
```java
class Solution {
    public int getSum(int a, int b) {
        int[] bits = new int[32];
        int cin = 0;

        for (int i = 0; i < 32; i++) {
            int a0 = a & 1;
            int b0 = b & 1;

            int a0_XOR_b0 = a0 ^ b0;
            int a0_AND_b0 = a0 & b0;

            bits[31 - i] = a0_XOR_b0 ^ cin;
            cin = a0_AND_b0 | (a0_XOR_b0 & cin);

            a >>= 1;
            b >>= 1;
        }

        int result = 0;
        for (int i = 0; i < 32; i++) {
            result = (result << 1) + bits[i];
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.32 MB (Beats: 38.34%)

<br>
