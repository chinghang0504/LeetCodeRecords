# [LeetCode Records](../../README.md) - Question 2042 Check if Numbers Are Ascending in a Sentence

### Attempt 1: Use two variables to store the previous and current numbers
```java
class Solution {
    public boolean areNumbersAscending(String s) {
        int prevNum = 0;
        int currNum = 0;

        for (char ch : s.toCharArray()) {
            if (ch >= '0' & ch <= '9') {
                currNum = currNum * 10 + (ch - '0');
            } else if (currNum != 0) {
                if (currNum <= prevNum) {
                    return false;
                } else {
                    prevNum = currNum;
                    currNum = 0;
                }
            }
        }

        if (currNum != 0 && currNum <= prevNum) {
            return false;
        } 

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.84 MB (Beats: 40.74%)

<br>
