# [LeetCode Records](../../README.md) - Question 1974 Minimum Time to Type Word Using Special Typewriter

### Attempt 1: Calculate the step of moving clockwise and counterclockwise
```java
class Solution {
    public int minTimeToType(String word) {
        int count = 0;
        int curr = 'a';

        for (char ch : word.toCharArray()) {

            if (ch > curr) {
                int clockwise = ch - curr;
                int counterclockwise = curr + 26 - ch;
                count += Math.min(clockwise, counterclockwise);
                curr = ch;
            } else if (ch < curr) {
                int clockwise = ch + 26 - curr;
                int counterclockwise = curr - ch;
                count += Math.min(clockwise, counterclockwise);
                curr = ch;
            }
            
            count++;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.51 MB (Beats: 17.42%)

<br>
