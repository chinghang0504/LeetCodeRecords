# [LeetCode Records](../../README.md) - Question 1276 Number of Burgers with No Waste of Ingredients

### Attempt 1: Solve the system of equations
```java
class Solution {
    public List<Integer> numOfBurgers(int tomatoSlices, int cheeseSlices) {
        if (tomatoSlices % 2 == 1) {
            return List.of();
        }

        int numOfJumbo = tomatoSlices / 2 - cheeseSlices;
        if (numOfJumbo < 0) {
            return List.of();
        }

        int numOfSmall = cheeseSlices - numOfJumbo;
        if (numOfSmall < 0) {
            return List.of();
        }

        return List.of(numOfJumbo, numOfSmall);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.94 MB (Beats: 93.43%)

<br>
