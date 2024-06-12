# [LeetCode Records](../../README.md) - Question 3110 Score of a String

### Attempt 1: Use a loop
```java
class Solution {
    public int scoreOfString(String s) {
        int sum = 0;
        char[] charArray = s.toCharArray();

        for (int i = 1; i < charArray.length; i++) {
            sum += Math.abs(charArray[i - 1] - charArray[i]);
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 99.54%)
- Memory: 41.44 MB (Beats: 96.41%)

<br>
