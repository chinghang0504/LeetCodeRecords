# [LeetCode Records](../../README.md) - Question 1189 Maximum Number of Balloons

### Attempt 1: Use an int[] to record the character counts
```java
class Solution {
    public int maxNumberOfBalloons(String text) {
        int[] counts = new int[26];

        for (char ch : text.toCharArray()) {
            counts[ch - 'a']++;
        }

        int bCount = counts['b' - 'a'];
        int aCount = counts['a' - 'a'];
        int lCount = counts['l' - 'a'] / 2;
        int oCount = counts['o' - 'a'] / 2;
        int nCount = counts['n' - 'a'];

        int min = bCount;
        if (aCount < min) {
            min = aCount;
        }
        if (lCount < min) {
            min = lCount;
        }
        if (oCount < min) {
            min = oCount;
        }
        if (nCount < min) {
            min = nCount;
        }
        
        return min;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.31 MB (Beats: 28.16%)

<br>
