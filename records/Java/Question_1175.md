# [LeetCode Records](../../README.md) - Question 1175 Prime Arrangements

### Attempt 1: Use a helper function to calculate the factorial
```java
class Solution {
    private int mod = 1_000_000_007;
    public int numPrimeArrangements(int n) {
        Set<Integer> primes = Set.of(2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97);

        Long primeNum = 0L;
        for (int i = 2; i <= n; i++) {
            if (primes.contains(i)) {
                primeNum++;
            }
        }

        Long nonPrimeNum = n - primeNum;

        return (int)(factorial(primeNum) * factorial(nonPrimeNum) % mod);
    }

    private Long factorial(Long n) {
        if (n == 0 || n == 1) {
            return 1L;
        }

        return n * factorial(n - 1) % mod;
    }
}
```
- Runtime: 1 ms (Beats: 35.58%)
- Memory: 40.43 MB (Beats: 34.97%)

<br>
