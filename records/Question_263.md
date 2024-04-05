# [LeetCode Records](../README.md) - Question 263 Ugly Number

### Attempt 1: Loop for dividing the number
```java
class Solution {
    public boolean isUgly(int n) {
        if (n <= 0) {
            return false;
        }

        while (n % 2 == 0) {
            n /= 2;
        }
        while (n % 3 == 0) {
            n /= 3;
        }
        while (n % 5 == 0) {
            n /= 5;
        }

        return n == 1;
    }
}
```
- Runtime: 1 ms (Beats: 48.21%)
- Memory: 41.05 MB (Beats: 13.70%)

<br>

### Attempt 2: Rearrange the order of division
```java
class Solution {
    public boolean isUgly(int n) {
        if (n <= 0) {
            return false;
        }

        while (n % 5 == 0) {
            n /= 5;
        }
        while (n % 3 == 0) {
            n /= 3;
        }
        while (n % 2 == 0) {
            n /= 2;
        }

        return n == 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.83 MB (Beats: 32.53%)

<br>
