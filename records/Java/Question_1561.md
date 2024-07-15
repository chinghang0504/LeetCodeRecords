# [LeetCode Records](../../README.md) - Question 1561 Maximum Number of Coins You Can Get

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public int maxCoins(int[] piles) {
        int n = piles.length / 3;

        Arrays.sort(piles);

        int sum = 0;
        for (int i = 0; i < n; i++) {
            sum += piles[piles.length - 2 - (i * 2)];
        }

        return sum;
    }
}
```
- Runtime: 27 ms (Beats: 64.02%)
- Memory: 56.23 MB (Beats: 60.96%)

<br>
