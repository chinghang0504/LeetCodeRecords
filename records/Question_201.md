# [LeetCode Records](../README.md) - Question 201 Bitwise AND of Numbers Range

### Attempt 1: Loop for each bit
```java
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        int result = 0;
        boolean isSame = true;

        for (int i = 0; i < 32; i++) {
            result <<= 1;

            int val1 = left << i >>> 31;
            int val2 = right << i >>> 31;

            if (isSame) {
                if (val1 == val2) {
                    result += val1;
                } else {
                    isSame = false;
                }
            }
        }

        return result;
    }
}
```
- Runtime: 4 ms (Beats: 14.81%)
- Memory: 43.43 MB (Beats: 91.41%)

<br>

### Attempt 2: Right shift first and then compare the values
```java
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        for (int i = 0; i < 31; i++) {
            int val1 = left >>> i;
            int val2 = right >>> i;
            if (val1 == val2) {
                return val1 << i;
            }
        }

        return 0;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.26 MB (Beats: 8.10%)

<br>
