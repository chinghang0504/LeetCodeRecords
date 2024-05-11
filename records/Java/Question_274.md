# [LeetCode Records](../../README.md) - Question 274 H-Index

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);

        int count = 0;
        for (int i = citations.length - 1; i >= 0; i--) {
            if (citations[i] >= count + 1) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 66.47%)
- Memory: 41.95 MB (Beats: 7.09%)

<br>
