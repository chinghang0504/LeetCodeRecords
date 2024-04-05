# [LeetCode Records](../README.md) - Question 342 Power of Four

### Attempt 1: Count the number of zeros on the right
```java
class Solution {
    public boolean isPowerOfFour(int n) {
        if (n <= 0) {
            return false;
        }
        
        int i = 0;
        for (; i < 31 && (n & 0x1) == 0; i++) {
            n >>>= 1;
        }

        return n == 0x1 && i % 2 == 0;
    }
}
```
- Runtime: 1 ms (Beats: 29.10%)
- Memory: 40.74 MB (Beats: 44.95%)

<br>

### Attempt 2: Use recursion
```java
class Solution {
    public boolean isPowerOfFour(int n) {
        if (n <= 0) {
            return false;
        }
        
        if (n == 1) {
            return true;
        }

        if (n % 4 == 0) {
            return isPowerOfFour(n / 4);
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.64 MB (Beats: 58.74%)

<br>
