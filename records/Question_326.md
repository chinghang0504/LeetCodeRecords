# [LeetCode Records](../README.md) - Question 326 Power of Three

### Attempt 1: 
```java
class Solution {
    public boolean isPowerOfThree(int n) {
        if (n <= 0) {
            return false;
        }

        while (n % 3 == 0) {
            n /= 3;
        }

        return n == 1;
    }
}
```
- Runtime: 8 ms (Beats: 90.19%)
- Memory: 44.04 MB (Beats: 38.68%)

<br>
