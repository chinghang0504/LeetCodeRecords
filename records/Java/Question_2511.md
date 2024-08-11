# [LeetCode Records](../../README.md) - Question 2511 Maximum Enemy Forts That Can Be Captured

### Attempt 1: Use a helper function to get the maximum of left and right counts
```java
class Solution {
    public int captureForts(int[] forts) {
        int maxCount = 0;

        for (int i = 0; i < forts.length; i++) {
            if (forts[i] == 1) {
                maxCount = Math.max(maxCount, getMaxCount(forts, i));
            }
        }

        return maxCount;
    }

    private int getMaxCount(int[] forts, int start) {
        int leftCount = 0;
        int rightCount = 0;

        int i = start - 1;
        while (i >= 0 && forts[i] == 0) {
            i--;
        }
        if (i >= 0 && forts[i] == -1) {
            leftCount = start - i - 1;
        }

        i = start + 1;
        while (i < forts.length && forts[i] == 0) {
            i++;
        }
        if (i < forts.length && forts[i] == -1) {
            rightCount = i - start - 1;
        }

        return Math.max(leftCount, rightCount);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.01 MB (Beats: 8.94%)

<br>
