# [LeetCode Records](../../README.md) - Question 2894 Divisible and Non-divisible Sums Difference

### Attempt 1: Use a loop
```java
class Solution {
    public int differenceOfSums(int n, int m) {
        int num1 = 0;
        int num2 = 0;

        for (int i = 1; i <= n; i++) {
            if (i % m == 0) {
                num2 += i;
            } else {
                num1 += i;
            }
        }

        return num1 - num2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.44 MB (Beats: 74.10%)

<br>

### Attempt 2: Use a mathematic formula
```java
class Solution {
    public int differenceOfSums(int n, int m) {
        int num1 = (1 + n) * n / 2;
        int num2 = 0;

        int multiplier = m;
        while (multiplier <= n) {
            num2 += multiplier;
            multiplier += m;
        }
        
        return num1 - num2 * 2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.65 MB (Beats: 43.47%)

<br>
