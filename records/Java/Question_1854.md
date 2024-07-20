# [LeetCode Records](../../README.md) - Question 1854 Maximum Population Year

### Attempt 1: Use an int[] and a nested loop to record the population
```java
class Solution {
    public int maximumPopulation(int[][] logs) {
        int[] counts = new int[2051];

        for (int[] log : logs) {
            for (int i = log[0]; i < log[1]; i++) {
                counts[i]++;
            }
        }

        int max = counts[1950];
        int maxYear = 1950;
        for (int i = 1951; i <= 2050; i++) {
            if (counts[i] > max) {
                max = counts[i];
                maxYear = i;
            }
        }

        return maxYear;
    }
}
```
- Runtime: 1 ms (Beats: 44.68%)
- Memory: 42.10 MB (Beats: 11.02%)

<br>

### Attempt 2: Use an int[] and a loop to record the change of population
```java
class Solution {
    public int maximumPopulation(int[][] logs) {
        int[] counts = new int[2051];

        for (int[] log : logs) {
            counts[log[0]]++;
            counts[log[1]]--;
        }

        int sum = counts[1950];
        int max = counts[1950];
        int maxYear = 1950;
        for (int i = 1951; i <= 2050; i++) {
            sum += counts[i];
            if (sum > max) {
                max = sum;
                maxYear = i;
            }
        }

        return maxYear;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.97 MB (Beats: 20.85%)

<br>
