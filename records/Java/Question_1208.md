# [LeetCode Records](../../README.md) - Question 1208 Get Equal Substrings Within Budget

### Attempt 1: Use a sliding window algorithm
```java
class Solution {
    public int equalSubstring(String s, String t, int maxCost) {
        char[] arr1 = s.toCharArray();
        char[] arr2 = t.toCharArray();
        int[] costs = new int[arr1.length];
        for (int i = 0; i < arr1.length; i++) {
            costs[i] = Math.abs(arr1[i] - arr2[i]);
        }

        int maxLen = 0;
        int currLen = 0;
        int currCost = 0;
        for (int i = 0; i < costs.length; i++) {
            int newCost = currCost + costs[i];
            if (newCost <= maxCost) {
                currCost = newCost;
                currLen++;
                maxLen = Math.max(maxLen, currLen);
            } else {
                currCost = newCost - costs[i - currLen];
            }
        }

        return maxLen;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 45.46 MB (Beats: 5.41%)

<br>
