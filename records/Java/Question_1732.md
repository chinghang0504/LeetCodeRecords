# [LeetCode Records](../../README.md) - Question 1732 Find the Highest Altitude

### Attempt 1: Use a loop
```java
class Solution {
    public int largestAltitude(int[] gain) {
        int curr = 0;
        int max = 0;

        for (int change : gain) {
            curr += change;
            max = Math.max(max, curr);
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.49 MB (Beats: 16.98%)

<br>
