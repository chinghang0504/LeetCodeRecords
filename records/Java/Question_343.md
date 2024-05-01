# [LeetCode Records](../../README.md) - Question 343 Integer Break

### Attempt 1: Calculate the max of each number of operands
```java
class Solution {
    public int integerBreak(int n) {
        int[] saved = new int[58];
        int max = 1;
        int product;

        for (int i = 2; i < n; i++) {
            int val = n / i;
            for (int j = 0; j < i; j++) {
                saved[j] = val;
            }
            int times = n - val * i;
            for (int j = 0; j < times; j++) {
                saved[j]++;
            }

            product = 1;
            for (int j = 0; j < i; j++) {
                product *= saved[j];
            }
            max = Math.max(max, product);
        }

        return max;
    }
}
```
- Runtime: 1 ms (Beats: 45.20%)
- Memory: 40.96 MB (Beats: 5.92%)

<br>
