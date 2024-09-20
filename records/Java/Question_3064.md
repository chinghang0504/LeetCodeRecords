# [LeetCode Records](../../README.md) - Question 3064 Guess the Number Using Bitwise Questions I

### Attempt 1: Test every bit position
```java
/** 
 * Definition of commonSetBits API (defined in the parent class Problem).
 * int commonSetBits(int num);
 */

public class Solution extends Problem {
    public int findNumber() {
        int[] binaryNumber = new int[32];

        int testNum = 1;
        for (int i = 0; i < 32; i++) {
            if (commonSetBits(testNum) > 0) {
                binaryNumber[32 - i - 1] = 1;
            }

            testNum <<= 1;
        }

        int sum = 0;
        for (int i = 0; i < 32; i++) {
            sum <<= 1;
            sum += binaryNumber[i];
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.14 MB (Beats: 37.50%)

<br>
