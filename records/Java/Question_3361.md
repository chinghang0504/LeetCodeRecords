# [LeetCode Records](../../README.md) - Question 3361 Shift Distance Between Two Strings

### Attempt 1: Use two long[] to store the prefix next costs and prefix previous costs
```java
class Solution {
    public long shiftDistance(String s, String t, int[] nextCost, int[] previousCost) {
        long[] prefixNextCosts = new long[27];
        long[] prefixPrevCosts = new long[27];
        for (int i = 0; i < 26; i++) {
            prefixNextCosts[i + 1] = prefixNextCosts[i] + nextCost[i];
            prefixPrevCosts[i + 1] = prefixPrevCosts[i] + previousCost[i];
        }

        char[] arr1 = s.toCharArray();
        char[] arr2 = t.toCharArray();
        long totalCost = 0;
        for (int i = 0; i < arr1.length; i++) {
            int startIndex = arr1[i] - 'a';
            int endIndex = arr2[i] - 'a';
            long currNextCost = 0;
            long currPrevCost = 0;

            if (startIndex > endIndex) {
                currNextCost = prefixNextCosts[26] - prefixNextCosts[startIndex] + prefixNextCosts[endIndex];
                currPrevCost = prefixPrevCosts[startIndex + 1] - prefixPrevCosts[endIndex + 1];
            } else if (arr1[i] < arr2[i]) {
                currNextCost = prefixNextCosts[endIndex] - prefixNextCosts[startIndex];
                currPrevCost = prefixPrevCosts[startIndex + 1] + prefixPrevCosts[26] - prefixPrevCosts[endIndex + 1];
            }

            totalCost += Math.min(currNextCost, currPrevCost);
        }

        return totalCost;
    }
}
```
- Runtime: 12 ms (Beats: 97.98%)
- Memory: 45.65 MB (Beats: 70.81%)

<br>
