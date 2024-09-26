# [LeetCode Records](../../README.md) - Question 1551 Minimum Operations to Make Array Equal

### Attempt 1: The average is n
```java
class Solution {
    public int minOperations(int n) {
        int total = 0;
        
        for (int i = 0; i < n; i++) {
            total += Math.abs(2 * i + 1 - n);
        }

        return total / 2;
    }
}
```
- Runtime: 1 ms (Beats: 51.97%)
- Memory: 40.54 MB (Beats: 48.03%)

<br>
