# [LeetCode Records](../../README.md) - Question 1109 Corporate Flight Bookings

### Attempt 1: Add all the bookings directly in the int[]
```java
class Solution {
    public int[] corpFlightBookings(int[][] bookings, int n) {
        int[] ans = new int[n];
        for (int[] booking : bookings) {
            for (int i = booking[0]; i <= booking[1]; i++) {
                ans[i - 1] += booking[2];
            }
        }

        return ans;
    }
}
```
- Runtime: 1115 ms (Beats: 10.08%)
- Memory: 59.44 MB (Beats: 75.83%)

<br>
