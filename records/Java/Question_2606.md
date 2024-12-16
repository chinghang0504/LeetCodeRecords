# [LeetCode Records](../../README.md) - Question 2606 Find the Substring With Maximum Cost

### Attempt 1: Use an int[] to store the character costs
```java
class Solution {
    public int maximumCostSubstring(String s, String chars, int[] vals) {
        int[] charCosts = new int[26];
        for (int i = 0; i < 26; i++) {
            charCosts[i] = i + 1;
        }

        char[] charsArr = chars.toCharArray();
        for (int i = 0; i < charsArr.length; i++) {
            charCosts[charsArr[i] - 'a'] = vals[i];
        }

        int maxCost = 0;
        int currCost = 0;
        for (char ch : s.toCharArray()) {
            int nextCost = currCost + charCosts[ch - 'a'];
            if (nextCost < 0) {
                currCost = 0;
            } else {
                currCost = nextCost;
                maxCost = Math.max(maxCost, currCost);
            }
        }

        return maxCost;
    }
}
```
- Runtime: 4 ms (Beats: 88.99%)
- Memory: 45.60 MB (Beats: 48.28%)

<br>
