# [LeetCode Records](../../README.md) - Question 3100 Water Bottles II

### Attempt 1: Use a while loop to execute each exchange
```java
class Solution {
    public int maxBottlesDrunk(int numBottles, int numExchange) {
        int drinkCount = numBottles;
        
        while (numBottles >= numExchange) {
            numBottles = numBottles - numExchange + 1;
            drinkCount++;
            numExchange++;
        }

        return drinkCount;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.68 MB (Beats: 68.57%)

<br>
