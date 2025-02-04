# [LeetCode Records](../../README.md) - Question 3442 Maximum Difference Between Even and Odd Frequency I

### Attempt 1: Use an int[] to store the character counts
```java
class Solution {
    public int maxDifference(String s) {
        int[] counts = new int[26];
        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        int minEvenCount = Integer.MAX_VALUE;
        int maxOddCount = Integer.MIN_VALUE;
        for (int count : counts) {
            if (count % 2 == 1) {
                maxOddCount = Math.max(maxOddCount, count);
            } else if (count > 0) {
                minEvenCount = Math.min(minEvenCount, count);
            }
        }

        return maxOddCount - minEvenCount;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.37 MB (Beats: 92.25%)

<br>
