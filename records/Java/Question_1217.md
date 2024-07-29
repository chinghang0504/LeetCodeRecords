# [LeetCode Records](../../README.md) - Question 1217 Minimum Cost to Move Chips to The Same Position

### Attempt 1: Get the odd and even position counts
```java
class Solution {
    public int minCostToMoveChips(int[] position) {
        int oddCounts = 0;
        int evenCounts = 0;

        for (int pos : position) {
            if (pos % 2 == 1) {
                oddCounts++;
            } else {
                evenCounts++;
            }
        }

        return Math.min(oddCounts, evenCounts);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.76 MB (Beats: 89.44%)

<br>
