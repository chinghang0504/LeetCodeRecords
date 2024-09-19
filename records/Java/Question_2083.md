# [LeetCode Records](../../README.md) - Question 2083 Substrings That Begin and End With the Same Letter

### Attempt 1: Use the formula of nCr
```java
class Solution {
    public long numberOfSubstrings(String s) {
        long[] counts = new long[26];

        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        long sum = 0;
        for (long count : counts) {
            sum += count + (count * count - count) / 2;
        }

        return sum;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.41 MB (Beats: 83.33%)

<br>
