# [LeetCode Records](../../README.md) - Question 1006 Clumsy Factorial

### Attempt 1: Simulate the process
```java
class Solution {
    public int clumsy(int n) {
        int sum = 0;
        int currSum = n;
        int operator = 0;
        for (int i = n - 1; i >= 1; i--) {
            if (operator == 0) {
                currSum *= i;
                operator++;
            } else if (operator == 1) {
                currSum /= i;
                operator++;
            } else if (operator == 2) {
                sum += currSum + i;
                currSum = 0;
                operator++;
            } else {
                currSum = -i;
                operator = 0;
            }
        }
        sum += currSum;

        return sum;
    }
}
```
- Runtime: 2 ms (Beats: 73.60%)
- Memory: 40.02 MB (Beats: 98.03%)

<br>
