# [LeetCode Records](../../README.md) - Question 1491 Average Salary Excluding the Minimum and Maximum Salary

### Attempt 1: Record the sum, the count, the min, and the max
```java
class Solution {
    public double average(int[] salary) {
        double sum = 0;
        int count = 0;
        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;

        for (int num : salary) {
            sum += num;
            count++;

            min = Math.min(min, num);
            max = Math.max(max, num);
        }

        return (sum - max - min) / (count - 2);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.45 MB (Beats: 20.44%)

<br>
