# [LeetCode Records](../../README.md) - Question 1167 Minimum Cost to Connect Sticks

### Attempt 1: Use a PriorityQueue to all the lengths of sticks
```java
class Solution {
    public int connectSticks(int[] sticks) {
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

        for (int stick : sticks) {
            priorityQueue.add(stick);
        }

        int sum = 0;
        while (priorityQueue.size() > 1) {
            int val1 = priorityQueue.poll();
            int val2 = priorityQueue.poll();
            int val = val1 + val2;

            sum += val;
            priorityQueue.add(val);
        }

        return sum;
    }
}
```
- Runtime: 63 ms (Beats: 45.02%)
- Memory: 45.00 MB (Beats: 64.23%)

<br>
