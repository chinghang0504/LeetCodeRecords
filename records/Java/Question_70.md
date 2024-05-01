# [LeetCode Records](../../README.md) - Question 70 Climbing Stairs

### Attempt 1: Use recursion and save the previous records
```java
class Solution {
    int[] records = new int[46];

    public int climbStairs(int n) {
        records[1] = 1;
        records[2] = 2;

        if (records[n] == 0) {
            records[n] = climbStairs(n - 1) + climbStairs(n - 2);
        }
        return records[n];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.26 MB (Beats: 50.78%)

<br>
