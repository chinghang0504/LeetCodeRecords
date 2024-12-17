# [LeetCode Records](../../README.md) - Question 2914 Minimum Number of Changes to Make Binary String Beautiful

### Attempt 1: Compare to the previous character
```java
class Solution {
    public int minChanges(String s) {
        char[] arr = s.toCharArray();

        int count = 0;
        for (int i = 1; i < arr.length; i += 2) {
            count += (arr[i - 1] + arr[i]) % 2;
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 99.79%)
- Memory: 45.29 MB (Beats: 6.70%)

<br>
