# [LeetCode Records](../../README.md) - Question 1578 Minimum Time to Make Rope Colorful

### Attempt 1: Use a helper function to calculate the total cost of the same colors and subtract from the maximum cost
```java
class Solution {
    public int minCost(String colors, int[] neededTime) {
        char[] arr = colors.toCharArray();

        int totalCost = 0;
        int i = 0;
        while (true) {
            while (i + 1 < arr.length && arr[i + 1] != arr[i]) {
                i++;
            }
            if (i >= arr.length - 1) {
                break;
            }

            int j = i;
            while (j + 1 < arr.length && arr[j + 1] == arr[i]) {
                j++;
            }
            totalCost += getCost(neededTime, i, j);
            i = j + 1;
        }

        return totalCost;
    }

    private int getCost(int[] neededTime, int start, int end) {
        int cost = 0;
        int maxCost = neededTime[start];
        for (int i = start; i <= end; i++) {
            cost += neededTime[i];
            maxCost = Math.max(maxCost, neededTime[i]);
        }
        
        return cost - maxCost;
    }
}
```
- Runtime: 5 ms (Beats: 99.73%)
- Memory: 59.26 MB (Beats: 90.50%)

<br>
