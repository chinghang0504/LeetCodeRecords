# [LeetCode Records](../../README.md) - Question 1486 XOR Operation in an Array

### Attempt 1: Use a loop
```java
class Solution {
    public int xorOperation(int n, int start) {
        int sum = 0;

        for (int i = 0; i < n; i++) {
            sum ^= start + i * 2;
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.69 MB (Beats: 9.24%)

<br>
