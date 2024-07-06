# [LeetCode Records](../../README.md) - Question 2278 Percentage of Letter in String

### Attempt 1: Use a loop
```java
class Solution {
    public int percentageLetter(String s, char letter) {
        int count = 0;
        char[] arr = s.toCharArray();

        for (char ch : arr) {
            if (ch == letter) {
                count++;
            }
        }

        return count * 100 / arr.length;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.33 MB (Beats: 34.78%)

<br>
