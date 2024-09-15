# [LeetCode Records](../../README.md) - Question 2079 Watering Plants

### Attempt 1: Use a while loop to execute each operation
```java
class Solution {
    public int wateringPlants(int[] plants, int capacity) {
        int currCapacity = capacity;
        int currPlantIndex = 0;
        int stepCount = 1;

        while (true) {
            currCapacity -= plants[currPlantIndex];
            currPlantIndex++;
            if (currPlantIndex >= plants.length) {
                return stepCount;
            }

            if (currCapacity < plants[currPlantIndex]) {
                currCapacity = capacity;
                stepCount += currPlantIndex * 2 + 1;
            } else {
                stepCount++;
            }           
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.81 MB (Beats: 9.61%)

<br>
