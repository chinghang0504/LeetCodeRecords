# [LeetCode Records](../../README.md) - Question 1304 Find N Unique Integers Sum up to Zero

### Attempt 1: Use the trivial solution
```java
class Solution {
    public int[] sumZero(int n) {
        int half = n / 2;
        int[] result = new int[n];
        int curr = 0;

        if (n % 2 == 0) {
            for (int i = -half; i < 0; i++) {
                result[curr] = i;
                curr++;
            }
            for (int i = 1; i <= half; i++) {
                result[curr] = i;
                curr++;
            }
        } else {
            for (int i = -half; i <= half; i++) {
                result[curr] = i;
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.09 MB (Beats: 97.35%)

<br>
