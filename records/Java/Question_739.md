# [LeetCode Records](../../README.md) - Question 739 Daily Temperatures

### Attempt 1: Use a PriorityQueue to store the previous temperature and its index
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int[] ans = new int[temperatures.length];
        PriorityQueue<int[]> priorityQueue = new PriorityQueue<>((t1, t2) -> t1[0] - t2[0]);

        for (int i = 0; i < temperatures.length; i++) {
            int[] itemInQueue = priorityQueue.peek();
            while (itemInQueue != null) {
                if (temperatures[i] > itemInQueue[0]) {
                    ans[itemInQueue[1]] = i - itemInQueue[1];
                    priorityQueue.poll();
                } else {
                    break;
                }

                itemInQueue = priorityQueue.peek();
            }

            priorityQueue.add(new int[]{ temperatures[i], i });
        }

        return ans;
    }
}
```
- Runtime: 74 ms (Beats: 33.61%)
- Memory: 56.01 MB (Beats: 97.77%)

<br>
