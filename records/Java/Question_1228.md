# [LeetCode Records](../../README.md) - Question 1228 Missing Number In Arithmetic Progression

### Attempt 1: Find the minimum difference first
```java
class Solution {
    public int missingNumber(int[] arr) {
        int diff1 = arr[1] - arr[0];
        int diff2 = arr[arr.length - 1] - arr[arr.length - 2];
        int diff = Math.abs(diff1) <= Math.abs(diff2) ? diff1 : diff2;

        for (int i = 0; i < arr.length - 1; i++) {
            int next = arr[i] + diff;
            if (next != arr[i + 1]) {
                return next;
            }
        }

        return arr[0];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.95 MB (Beats: 77.27%)

<br>
