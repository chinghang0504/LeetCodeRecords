# [LeetCode Records](../../README.md) - Question 1952 Three Divisors

### Attempt 1: Use a loop to test every case
```java
class Solution {
    public boolean isThree(int n) {
        int count = 0;

        for (int i = 1; i <= n; i++) {
            if (n % i == 0) {
                count++;
            }
        }

        return count == 3;
    }
}
```
- Runtime: 1 ms (Beats: 64.49%)
- Memory: 40.33 MB (Beats: 40.45%)

<br>
