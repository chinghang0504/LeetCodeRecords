# [LeetCode Records](../../README.md) - Question 57 Insert Interval

### Attempt 1: Add the new interval in the sorted list and merge the intervals
```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        int newSize = intervals.length + 1;
        List<int[]> list = new ArrayList<>(newSize);
        
        int i = 0;
        while (i < intervals.length && intervals[i][0] < newInterval[0]) {
            list.add(intervals[i]);
            i++;
        }
        list.add(newInterval);
        while (i < intervals.length) {
            list.add(intervals[i]);
            i++;
        }

        List<int[]> nextList = new ArrayList<>(newSize);
        int[] lastInterval = list.get(0);
        nextList.add(lastInterval);

        for (int j = 1; j < newSize; j++) {
            int[] interval = list.get(j);
            if (interval[0] <= lastInterval[1]) {
                lastInterval[1] = Math.max(lastInterval[1], interval[1]);
            } else {
                lastInterval = interval;
                nextList.add(lastInterval);
            }
        }

        return nextList.toArray(int[][]::new);
    }
}
```
- Runtime: 1 ms (Beats: 98.79%)
- Memory: 44.71 MB (Beats: 62.61%)

<br>
