# [LeetCode Records](../../README.md) - Question 762 Prime Number of Set Bits in Binary Representation

### Attempt 1: Use a helper function
```java
class Solution {
    public int countPrimeSetBits(int left, int right) {
        int count = 0;

        for (int i = left; i <= right; i++) {
            if (isPrimeSetBits(i)) {
                count++;
            }
        }

        return count;
    }

    private boolean isPrimeSetBits(int num) {
        int n = 0;
        
        while (num > 0) {
            n += num & 1;
            num >>>= 1;
        }

        for (int i = 2; i <= n / 2; i++) {
            if (n % i == 0) {
                return false;
            }
        }

        return n > 1;
    }
}
```
- Runtime: 12 ms (Beats: 58.34%)
- Memory: 40.19 MB (Beats: 82.94%)

<br>
