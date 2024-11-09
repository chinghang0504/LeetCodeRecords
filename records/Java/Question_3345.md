# [LeetCode Records](../../README.md) - Question 3345 Smallest Divisible Digit Product I

### Attempt 1: Test every case
```java
class Solution {
    public int smallestNumber(int n, int t) {
        int productOfDigits = getProductOfDigits(n);
        while (productOfDigits % t != 0) {
            n++;
            productOfDigits = getProductOfDigits(n);
        }

        return n;
    }

    private int getProductOfDigits(int n) {
        if (n == 0) {
            return 0;
        }

        int productOfDigits = 1;
        while (n > 0) {
            productOfDigits *= n % 10;
            n /= 10;
        }
        
        return productOfDigits;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.28 MB (Beats: 100.00%)

<br>
