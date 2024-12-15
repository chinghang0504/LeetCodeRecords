# [LeetCode Records](../../README.md) - Question 3386 Button with Longest Push Time

### Attempt 1: Use a HashMap to store the index and its max time key-value pairs
```java
class Solution {
    public int buttonWithLongestTime(int[][] events) {
        Map<Integer, Integer> map = new HashMap<>();

        map.put(events[0][0], events[0][1]);
        for (int i = 1; i < events.length; i++) {
            int time = events[i][1] - events[i - 1][1];
            Integer prevMaxTime = map.get(events[i][0]);
            if (prevMaxTime == null || time > prevMaxTime) {
                map.put(events[i][0], time);
            }
        }

        int maxTime = 0;
        int minIndex = 0;
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            int time = entry.getValue();
            if (time > maxTime) {
                maxTime = time;
                minIndex = entry.getKey();
            } else if (time == maxTime) {
                minIndex = Math.min(minIndex, entry.getKey());
            }
        }

        return minIndex;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.70 MB (Beats: 100.00%)

<br>
