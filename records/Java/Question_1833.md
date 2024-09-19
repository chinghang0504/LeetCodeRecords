# [LeetCode Records](../../README.md) - Question 1833 Maximum Ice Cream Bars

### Attempt 1: Use Arrays.sort() to sort the array first
```java
class Solution {
    public int maxIceCream(int[] costs, int coins) {
        Arrays.sort(costs);

        int count = 0;
        for (int i = 0; i < costs.length; i++) {
            if (costs[i] <= coins) {
                coins -= costs[i];
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 32 ms (Beats: 83.69%)
- Memory: 61.34 MB (Beats: 50.91%)

<br>
