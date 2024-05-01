# [LeetCode Records](../../README.md) - Question 252 Meeting Rooms

### Attempt 1: Sort the intervals first
```java
class Solution {
    public boolean canAttendMeetings(int[][] intervals) {
        Arrays.sort(intervals, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                if (o1[0] < o2[0]) {
                    return -1;
                } else if (o1[0] == o2[0]) {
                    return 0;
                } else {
                    return 1;
                }
            }
        });

        for (int i = 0; i < intervals.length - 1; i++) {
            if (intervals[i][1] > intervals[i + 1][0]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 6 ms (Beats: 81.16%)
- Memory: 45.92 MB (Beats: 46.77%)

<br>
