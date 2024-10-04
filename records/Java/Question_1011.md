# [LeetCode Records](../../README.md) - Question 1011 Capacity To Ship Packages Within D Days

### Attempt 1: Use binary search to find the maximum weight of each day
```java
class Solution {
    public int shipWithinDays(int[] weights, int days) {
        int maxWeight = 0;
        int totalWeight = 0;
        for (int weight : weights) {
            maxWeight = Math.max(maxWeight, weight);
            totalWeight += weight;
        }

        int lower = maxWeight;
        int upper = totalWeight;
        while (lower < upper) {
            int middle = (lower + upper) / 2;
            if (isAbleToShip(weights, days, middle)) {
                upper = middle;
            } else {
                lower = middle + 1;
            }
        }

        return upper;
    }

    private boolean isAbleToShip(int[] weights, int days, int maxWeight) {
        int currWeight = 0;
        int day = 0;
        int i = 0;
        while (i < weights.length && day < days) {
            int nextWeight = currWeight + weights[i];
            if (nextWeight > maxWeight) {
                currWeight = weights[i];
                day++;
            } else {
                currWeight += weights[i];
            }

            i++;
        }
        
        return i == weights.length && day < days;
    }
}
```
- Runtime: 11 ms (Beats: 76.05%)
- Memory: 46.73 MB (Beats: 92.18%)

<br>
