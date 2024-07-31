# [LeetCode Records](../../README.md) - Question 2582 Pass the Pillow

### Attempt 1: Calculate the number of rounds and steps
```java
class Solution {
    public int passThePillow(int n, int time) {
        int round = (time - 1) / (n - 1);
        int step = time % (n - 1);

        if (round % 2 == 0) {
            if (step == 0) {
                return n;
            } else {
                return 1 + step;
            }
        } else {
            if (step == 0) {
                return 1;
            } else {
                return n - step;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.30 MB (Beats: 48.81%)

<br>
