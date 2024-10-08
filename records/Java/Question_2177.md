# [LeetCode Records](../../README.md) - Question 2177 Find Three Consecutive Integers That Sum to a Given Number

### Attempt 1: Check if the number is divisible by 3
```java
class Solution {
    public long[] sumOfThree(long num) {
        if (num % 3 != 0) {
            return new long[0];
        }

        long[] ans = new long[3];
        long average = num / 3;
        for (int i = 0; i < 3; i++) {
            ans[i] = average;
        }
        ans[0]--;
        ans[2]++;

        return ans;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.24 MB (Beats: 90.43%)

<br>
