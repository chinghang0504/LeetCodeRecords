# [LeetCode Records](../../README.md) - Question 2644 Find the Maximum Divisibility Score

### Attempt 1: Use an int[] to save the divisor scores
```java
class Solution {
    public int maxDivScore(int[] nums, int[] divisors) {
        int[] divisorScores = new int[divisors.length];
        
        for (int i = 0; i < divisors.length; i++) {
            for (int num : nums) {
                if (num % divisors[i] == 0) {
                    divisorScores[i]++;
                }
            }
        }

        int maxScores = divisorScores[0];
        int minDivisor = divisors[0];

        for (int i = 1; i < divisorScores.length; i++) {
            if (divisorScores[i] > maxScores) {
                maxScores = divisorScores[i];
                minDivisor = divisors[i];
            } else if (divisorScores[i] == maxScores) {
                minDivisor = Math.min(minDivisor, divisors[i]);
            }
        }

        return minDivisor;
    }
}
```
- Runtime: 175 ms (Beats: 94.21%)
- Memory: 45.22 MB (Beats: 11.58%)

<br>
