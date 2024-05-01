# [LeetCode Records](../../README.md) - Question 204 Count Primes

### Attempt 1: Use Sieve of Eratosthenes
```java
class Solution {
    public int countPrimes(int n) {
        if (n == 0 || n == 1) {
            return 0;
        }

        boolean[] isNotPrime = new boolean[n];
        int count = 0;
        for (int j = 2; j < n; j++) {
            if (isNotPrime[j]) {
                continue;
            }
            
            count++;

            for (int i = j + j; i < n; i += j) {
                isNotPrime[i] = true;
            }
        }

        return count;
    }
}
```
- Runtime: 107 ms (Beats: 41.50%)
- Memory: 49.07 MB (Beats: 52.84%)

<br>
