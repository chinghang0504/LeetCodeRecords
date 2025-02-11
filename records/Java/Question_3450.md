# [LeetCode Records](../../README.md) - Question 3450 Maximum Students on a Single Bench

### Attempt 1: Use a HashMap to store the benchId and its student id set key-value pairs
```java
class Solution {
    public int maxStudentsOnBench(int[][] students) {
        Map<Integer, Set<Integer>> idToBench = new HashMap<>();

        int maxBench = 0;
        for (int[] student : students) {
            Set<Integer> bench = idToBench.get(student[1]);
            if (bench == null) {
                bench = new HashSet<>();
                idToBench.put(student[1], bench);
            }

            bench.add(student[0]);
            maxBench = Math.max(maxBench, bench.size());
        }

        return maxBench;
    }
}
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 45.02 MB (Beats: 100.00%)

<br>
