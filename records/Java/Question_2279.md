# [LeetCode Records](../../README.md) - Question 2279 Maximum Bags With Full Capacity of Rocks

### Attempt 1: Calculate the remainder for each bag
```java
class Solution {
    public int maximumBags(int[] capacity, int[] rocks, int additionalRocks) {
        int n = capacity.length;
        for (int i = 0; i < n; i++) {
            capacity[i] -= rocks[i];
        }

        Arrays.sort(capacity);
        
        int count = 0;
        for (int i = 0; i < n && additionalRocks > 0; i++) {
            if (capacity[i] == 0) {
                count++;
            } else if (additionalRocks >= capacity[i]) {
                additionalRocks -= capacity[i];
                count++;
            } else {
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 13 ms (Beats: 98.24%)
- Memory: 54.91 MB (Beats: 85.92%)

<br>
