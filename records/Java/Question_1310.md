# [LeetCode Records](../../README.md) - Question 1310 XOR Queries of a Subarray

### Attempt 1: Use an int[] to store the accumulative XOR values
```java
class Solution {
    public int[] xorQueries(int[] arr, int[][] queries) {
        int[] accumulativeXOR = new int[arr.length + 1];

        int val = 0;
        for (int i = 0; i < arr.length; i++) {
            val ^= arr[i];
            accumulativeXOR[i + 1] = val;
        }

        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int start = queries[i][0];
            int end = queries[i][1];

            ans[i] = start == end ? arr[start] : accumulativeXOR[end + 1] ^ accumulativeXOR[start];
        }

        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 99.95%)
- Memory: 59.81 MB (Beats: 8.43%)

<br>
