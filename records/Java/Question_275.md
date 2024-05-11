# [LeetCode Records](../../README.md) - Question 275 H-Index II

### Attempt 1: Use binary search
```java
class Solution {
    public int hIndex(int[] citations) {
        int low = 0;
        int high = citations.length - 1;
        int max = 0;

        while (low <= high) {
            int middle = (low + high) / 2;
            int paperNum = citations.length - middle;
            if (citations[middle] >= paperNum) {
                max = Math.max(max, paperNum);
                high = middle - 1;
            } else {
                low = middle + 1;
            }
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 48.29 MB (Beats: 6.99%)

<br>
