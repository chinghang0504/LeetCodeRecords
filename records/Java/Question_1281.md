# [LeetCode Records](../../README.md) - Question 1281 Subtract the Product and Sum of Digits of an Integer

### Attempt 1: 
```java
class Solution {
    public int subtractProductAndSum(int n) {
        int product = 1;
        int sum = 0;

        while (n > 0) {
            int last = n % 10;
            product *= last;
            sum += last;

            n /= 10;
        }

        return product - sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.29 MB (Beats: 51.45%)

<br>
