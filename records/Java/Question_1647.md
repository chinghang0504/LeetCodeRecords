# [LeetCode Records](../../README.md) - Question 1647 Minimum Deletions to Make Character Frequencies Unique

### Attempt 1: Use an int[] to store the character counts
```java
class Solution {
    public int minDeletions(String s) {
        int[] counts = new int[26];
        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        Arrays.sort(counts);

        int actionCount = 0;
        int lowestAvailableCount = counts[25] - 1;
        for (int i = 24; i >= 0; i--) {
            if (lowestAvailableCount > 0) {
                if (counts[i] > lowestAvailableCount) {
                    actionCount += (counts[i] - lowestAvailableCount);
                    lowestAvailableCount--;
                } else if (counts[i] == lowestAvailableCount) {
                    lowestAvailableCount--;
                } else {
                    lowestAvailableCount = counts[i] - 1;
                }
            } else {
                actionCount += counts[i];
            }
        }

        return actionCount;
    }
}
```
- Runtime: 7 ms (Beats: 98.70%)
- Memory: 45.34 MB (Beats: 55.84%)

<br>
