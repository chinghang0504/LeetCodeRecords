# [LeetCode Records](../../README.md) - Question 1395 Count Number of Teams

### Attempt 1: Test every case
```java
class Solution {
    public int numTeams(int[] rating) {
        int count = 0;

        for (int i = 0; i < rating.length - 2; i++) {
            for (int j = i + 1; j < rating.length - 1; j++) {
                for (int k = j + 1; k < rating.length; k++) {
                    if ((rating[i] < rating[j] && rating[j] < rating[k]) ||
                        (rating[i] > rating[j] && rating[j] > rating[k])) {
                        count++;
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 2212 ms (Beats: 7.24%)
- Memory: 42.28 MB (Beats: 71.21%)

<br>
