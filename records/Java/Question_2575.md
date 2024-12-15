# [LeetCode Records](../../README.md) - Question 2575 Find the Divisibility Array of a String

### Attempt 1: Use % operator
```java
class Solution {
    public int[] divisibilityArray(String word, int m) {
        char[] arr = word.toCharArray();
        long val = 0;
        int[] ans = new int[arr.length];

        for (int i = 0; i < arr.length; i++) {
            val = (val * 10 + arr[i] - '0') % m;
            ans[i] = val == 0 ? 1 : 0;
        }

        return ans;
    }
}
```
- Runtime: 7 ms (Beats: 85.47%)
- Memory: 56.85 MB (Beats: 90.86%)

<br>
