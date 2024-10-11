# [LeetCode Records](../../README.md) - Question 2244 Minimum Rounds to Complete All Tasks

### Attempt 1: Use a HashMap to store the task and the count key-value pairs
```java
class Solution {
    public int minimumRounds(int[] tasks) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int task : tasks) {
            map.merge(task, 1, Integer::sum);
        }

        int round = 0;
        for (int count : map.values()) {
            if (count == 1) {
                return -1;
            }

            int remainder = count % 3;
            round += remainder == 0 ? count / 3 : count / 3 + 1;
        }

        return round;
    }
}
```
- Runtime: 23 ms (Beats: 92.98%)
- Memory: 62.26 MB (Beats: 11.06%)

<br>
