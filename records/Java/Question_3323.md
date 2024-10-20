# [LeetCode Records](../../README.md) - Question 3323 Minimize Connected Groups by Inserting Interval

### Attempt 1: Use Arrays.sort() to sort the intervals, merge the intervals, and sliding window technique to find the maximum count
```java
class Solution {
    public int minConnectedGroups(int[][] intervals, int k) {
        Arrays.sort(intervals, (interval1, interval2) -> interval1[0] - interval2[0]);

        List<int[]> list = new ArrayList<>();
        int[] lastInterval = intervals[0];
        list.add(lastInterval);
        
        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] <= lastInterval[1]) {
                lastInterval[1] = Math.max(lastInterval[1], intervals[i][1]);
            } else {
                lastInterval = intervals[i];
                list.add(lastInterval);
            }
        }

        int size = list.size();
        int startIndex = 0;
        int[] startInterval = list.get(startIndex);
        int count = 0;
        while (startIndex < size) {
            int nextIndex = startIndex + count + 1;
            if (nextIndex >= size) {
                break;
            }

            int[] endInterval = list.get(nextIndex);
            if (endInterval[0] - startInterval[1] <= k) {
                count++;
            } else {
                startIndex++;
                if (startIndex >= size) {
                    break;
                }
                startInterval = list.get(startIndex);
            }
        }

        return size - count;
    }
}
```
- Runtime: 88 ms (Beats: 100.00%)
- Memory: 105.41 MB (Beats: 41.46%)

<br>
