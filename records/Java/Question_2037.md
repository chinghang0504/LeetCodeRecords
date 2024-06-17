# [LeetCode Records](../../README.md) - Question 2037 Minimum Number of Moves to Seat Everyone

### Attempt 1: Use Arrays.sort() twice
```java
class Solution {
    public int minMovesToSeat(int[] seats, int[] students) {
        int n = seats.length;

        Arrays.sort(seats);
        Arrays.sort(students);

        int count = 0;

        for (int i = 0; i < n; i++) {
            count += Math.abs(students[i] - seats[i]);
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 51.50%)
- Memory: 43.87 MB (Beats: 77.10%)

<br>
