# [LeetCode Records](../../README.md) - Question 1837 Sum of Digits in Base K

### Attempt 1: 
```java
class Solution {
    public int sumBase(int n, int k) {
        int sum = 0;

        while (n >= k) {
            sum += n % k;
            n /= k;
        }
        sum += n;

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.16 MB (Beats: 60.96%)

<br>
