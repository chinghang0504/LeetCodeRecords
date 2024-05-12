# [LeetCode Records](../../README.md) - Question 370 Range Addition

### Attempt 1: Use two loops
```java
class Solution {
    public int[] getModifiedArray(int length, int[][] updates) {
        int[] arr = new int[length];

        for (int[] update : updates) {
            for (int i = update[0]; i <= update[1]; i++) {
                arr[i] += update[2];
            }
        }

        return arr;
    }
}
```
- Runtime: 562 ms (Beats: 6.22%)
- Memory: 49.75 MB (Beats: 79.90%)

<br>
