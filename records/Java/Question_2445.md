# [LeetCode Records](../../README.md) - Question 2445 Number of Nodes With Value One

### Attempt 1: Use an int[] to store the root counts
```java
class Solution {
    public int numberOfNodes(int n, int[] queries) {
        int[] counts = new int[n];

        for (int query : queries) {
            counts[query - 1]++;
        }

        int count = 0;
        for (int i = 0; i < n; i++) {
            int root = i + 1;
            int localCount = 0;

            while (root >= 1) {
                localCount += counts[root - 1];
                root /= 2;
            }

            if (localCount % 2 == 1) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 35 ms (Beats: 44.74%)
- Memory: 55.70 MB (Beats: 81.58%)

<br>
