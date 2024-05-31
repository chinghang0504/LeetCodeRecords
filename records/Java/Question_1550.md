# [LeetCode Records](../../README.md) - Question 1550 Three Consecutive Odds

### Attempt 1: Tracing the number of consecutive odds
```java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
        int count = 0;
        
        for (int num : arr) {
            if (num % 2 == 1) {
                count++;
                if (count == 3) {
                    return true;
                }
            } else {
                count = 0;
            }
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.23 MB (Beats: 32.12%)

<br>
