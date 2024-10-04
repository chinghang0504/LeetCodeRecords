# [LeetCode Records](../../README.md) - Question 2895 Minimum Processing Time

### Attempt 1: Sort the processor time and the tasks
```java
class Solution {
    public int minProcessingTime(List<Integer> processorTime, List<Integer> tasks) {
        processorTime.sort(Collections.reverseOrder(Integer::compareTo));
        tasks.sort(Integer::compareTo);

        int maxTime = 0;
        int size = processorTime.size();
        for (int i = 0; i < size; i++) {
            maxTime = Math.max(maxTime, processorTime.get(i) + tasks.get(i * 4 + 3));
        }

        return maxTime;
    }
}
```
- Runtime: 73 ms (Beats: 45.73%)
- Memory: 59.07 MB (Beats: 67.95%)

<br>
