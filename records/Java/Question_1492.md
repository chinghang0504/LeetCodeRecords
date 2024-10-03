# [LeetCode Records](../../README.md) - Question 1492 The kth Factor of n

### Attempt 1: Use a loop to test every case
```java
class Solution {
    public int kthFactor(int n, int k) {
        int count = 0;
        for (int i = 1; i <= n; i++) {
            if (n % i == 0) {
                count++;

                if (count == k) {
                    return i;
                }
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.88 MB (Beats: 10.84%)

<br>
