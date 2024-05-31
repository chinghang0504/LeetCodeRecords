# [LeetCode Records](../../README.md) - Question 1518 Water Bottles

### Attempt 1: Keep tracing the full and empty bottles
```java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        int drinkBottles = 0;
        int emptyBottles = 0;

        while (numBottles > 0) {
            drinkBottles += numBottles;
            emptyBottles += numBottles;

            numBottles = emptyBottles / numExchange;
            emptyBottles -= numBottles * numExchange;
        }

        return drinkBottles;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.42 MB (Beats: 23.89%)

<br>
