# [LeetCode Records](../../README.md) - Question 2564 Substring XOR Queries

### Attempt 1: Use a HashMap to store the binary string and its start index key-value pairs
```java
class Solution {
    public int[][] substringXorQueries(String s, int[][] queries) {
        int len = s.length();
        int minLen = Math.min(len, 30);
        Map<String, Integer> map = new HashMap<>();
        for (int i = 1; i <= minLen; i++) {
            for (int j = 0; j < len - i + 1; j++) {
                map.merge(s.substring(j, j + i), j, Integer::min);
            }
        }

        int[][] ans = new int[queries.length][2];
        for (int i = 0; i < queries.length; i++) {
            int val = queries[i][0] ^ queries[i][1];
            String targetStr = Integer.toBinaryString(val);
            Integer startIndex = map.get(targetStr);
            if (startIndex == null) {
                ans[i][0] = -1;
                ans[i][1] = -1;
            } else {
                ans[i][0] = startIndex;
                ans[i][1] = startIndex + targetStr.length() - 1;
            }
        }

        return ans;
    }
}
```
- Runtime: 81 ms (Beats: 15.07%)
- Memory: 81.78 MB (Beats: 64.00%)

<br>
