# [LeetCode Records](../../README.md) - Question 1422 Maximum Score After Splitting a String

### Attempt 1: Use a loop that tests each case
```java
class Solution {
    public int maxScore(String s) {
        char[] arr = s.toCharArray();
        int leftScore = arr[0] == '0' ? 1 : 0;
        int rightScore = 0;
        int maxScore = 0;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] == '1') {
                rightScore++;
            }
        }
        maxScore = leftScore + rightScore;

        for (int i = 1; i < arr.length - 1; i++) {
            if (arr[i] == '0') {
                leftScore++;
            } else {
                rightScore--;
            }

            maxScore = Math.max(maxScore, leftScore + rightScore);
        }

        return maxScore;
    }
}
```
- Runtime: 1 ms (Beats: 99.04%)
- Memory: 41.30 MB (Beats: 66.51%)

<br>
