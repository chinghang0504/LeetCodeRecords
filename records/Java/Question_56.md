# [LeetCode Records](../../README.md) - Question 56 Merge Intervals

### Attempt 1: Use Arrays.sort() to sort the intervals
```java
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (interval1, interval2) -> interval1[0] - interval2[0]);

        List<int[]> list = new ArrayList<>();
        list.add(intervals[0]);
        
        int[] lastInterval = intervals[0];
        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] <= lastInterval[1]) {
                lastInterval[1] = Math.max(lastInterval[1], intervals[i][1]);
            } else {
                list.add(intervals[i]);
                lastInterval = intervals[i];
            }
        }

        return list.toArray(int[][]::new);
    }
}
```
- Runtime: 8 ms (Beats: 87.69%)
- Memory: 46.24 MB (Beats: 83.23%)

<br>
