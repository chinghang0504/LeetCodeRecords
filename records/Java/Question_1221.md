# [LeetCode Records](../../README.md) - Question 1221 Split a String in Balanced Strings

### Attempt 1: Keep tracking the number of L and R on the left and right
```java
class Solution {
    public int balancedStringSplit(String s) {
        int size = s.length();
        int leftL = 0;
        int leftR = 0;
        int rightL = size / 2;
        int rightR = size / 2;
        int count = 0;
        int startIndex = 0;

        while (startIndex < size) {
            char ch = s.charAt(startIndex);
            if (ch == 'L') {
                leftL++;
                rightL--;
            } else {
                leftR++;
                rightR--;
            }

            if (leftL == leftR && rightL == rightR) {
                count++;
                leftL = 0;
                leftR = 0;
            }
            
            startIndex++;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.54 MB (Beats: 10.01%)

<br>
