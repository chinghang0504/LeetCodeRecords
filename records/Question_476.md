# [LeetCode Records](../README.md) - Question 476 Number Complement

### Attempt 1: Use an int array to record the binary digits
```java
class Solution {
    public int findComplement(int num) {
        int[] saved = new int[32];
        int count = 0;

        while (num != 0) {
            saved[count++] = (num & 0x1) == 1 ? 0 : 1;
            num >>>= 1;
        }

        int result = 0;
        for (int i = count - 1; i >= 0; i--) {
            result <<= 1;
            result += saved[i];
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.08 MB (Beats: 88.27%)

<br>
