# [LeetCode Records](../../README.md) - Question 1272 Remove Interval

### Attempt 1: Check if the intervals are intersected
```java
class Solution {
    public List<List<Integer>> removeInterval(int[][] intervals, int[] toBeRemoved) {
        List<List<Integer>> ans = new ArrayList<>();

        for (int[] interval : intervals) {
            int start = Math.max(interval[0], toBeRemoved[0]);
            int end = Math.min(interval[1], toBeRemoved[1]);

            if (start < end) {
                if (interval[0] < start) {
                    ans.add(List.of(interval[0], start));
                }
                if (interval[1] > end) {
                    ans.add(List.of(end, interval[1]));
                }
            } else {
                ans.add(List.of(interval[0], interval[1]));
            }
        }

        return ans;
    }
}
```
- Runtime: 9 ms (Beats: 70.34%)
- Memory: 54.45 MB (Beats: 84.14%)

<br>
