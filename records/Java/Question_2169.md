# [LeetCode Records](../../README.md) - Question 2169 Count Operations to Obtain Zero

### Attempt 1: Use a loop
```java
class Solution {
    public int countOperations(int num1, int num2) {
        int count = 0;

        while (num1 != 0 && num2 != 0) {
            if (num1 >= num2) {
                num1 -= num2;
            } else {
                num2 -= num1;
            }

            count++;
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 93.69%)
- Memory: 40.27 MB (Beats: 57.61%)

<br>
