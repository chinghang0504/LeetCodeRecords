# [LeetCode Records](../../README.md) - Question 3168 Minimum Number of Chairs in a Waiting Room

### Attempt 1: Update the maximum count
```java
class Solution {
    public int minimumChairs(String s) {
        int count = 0;
        int max = 0;

        for (char ch : s.toCharArray()) {
            if (ch == 'E') {
                count++;
                max = Math.max(max, count);
            } else {
                count--;
            }
        }

        return max;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.89 MB (Beats: 83.34%)

<br>
