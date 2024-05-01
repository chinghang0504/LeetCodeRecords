# [LeetCode Records](../../README.md) - Question 7 Reverse Integer

### Attempt 1: Use ArithmeticException to detect overflow
```java
class Solution {
    public int reverse(int x) {
        int sum = 0;
        boolean orgPositive = x >= 0;

        try {
            while (x != 0) {
                sum = Math.multiplyExact(sum, 10);
                sum = Math.addExact(sum, x % 10);
                x /= 10;
            }
        } catch (ArithmeticException e) {
            return 0;
        }
        
        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 85.66%)
- Memory: 40.90 MB (Beats: 45.18%)

<br>

### Attempt 2: Use the previous sum to check overflow
```java
class Solution {
    public int reverse(int x) {
        int sum = 0;
        boolean orgPositive = x >= 0;
        int pervSum = 0;

        while (x != 0) {
            sum *= 10;
            sum += x % 10;
            if (sum / 10 != pervSum) {
                return 0;
            }

            x /= 10;
            pervSum = sum;
        }
        
        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 85.66%)
- Memory: 40.88 MB (Beats: 45.18%)

<br>
