# [LeetCode Records](../../README.md) - Question 3199 Count Triplets with Even XOR Set Bits I

### Attempt 1: Use a helper function that check if it has an even number of set bits
```java
class Solution {
    public int tripletCount(int[] a, int[] b, int[] c) {
        int count = 0;

        for (int num1 : a) {
            for (int num2 : b) {
                for (int num3 : c) {
                    if (isEvenSetBits(num1 ^ num2 ^ num3)) {
                        count++;
                    }
                }
            }
        }

        return count;
    }

    private boolean isEvenSetBits(int num) {
        int count = 0;

        while (num > 0) {
            count += num & 1;
            num >>>= 1;
        }

        return count % 2 == 0;
    }
}
```
- Runtime: 114 ms (Beats: 25.93%)
- Memory: 44.33 MB (Beats: 37.04%)

<br>
