# [LeetCode Records](../../README.md) - Question 2028 Find Missing Observations

### Attempt 1: Simulate the process and calculate the average and the remainder
```java
class Solution {
    public int[] missingRolls(int[] rolls, int mean, int n) {
        int remainder = mean * (rolls.length + n);
        for (int num : rolls) {
            remainder -= num;
        }

        int avg = remainder / n;
        if (avg < 1 || avg > 6) {
            return new int[0];
        }

        int[] ans = new int[n];
        for (int i = 0; i < n; i++) {
            ans[i] = avg;
            remainder -= avg;
        }
        if (remainder > 0 && avg == 6) {
            return new int[0];
        }
        for (int i = 0; i < remainder; i++) {
            ans[i]++;
        }

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 99.31%)
- Memory: 58.69 MB (Beats: 97.59%)

<br>
