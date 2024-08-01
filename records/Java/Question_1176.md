# [LeetCode Records](../../README.md) - Question 1176 Diet Plan Performance

### Attempt 1: Use a nested loop to calculate the local sum
```java
class Solution {
    public int dietPlanPerformance(int[] calories, int k, int lower, int upper) {
        int sum = 0;

        for (int i = 0; i < calories.length - k + 1; i++) {
            int localSum = 0;
            for (int j = 0; j < k; j++) {
                localSum += calories[i + j];
            }

            if (localSum > upper) {
                sum++;
            } else if (localSum < lower) {
                sum--;
            }
        }

        return sum;
    }
}
```
- Runtime: 1465 ms (Beats: 17.65%)
- Memory: 48.79 MB (Beats: 66.18%)

<br>
