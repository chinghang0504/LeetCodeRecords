# [LeetCode Records](../../README.md) - Question 2335 Minimum Amount of Time to Fill Cups

### Attempt 1: Fill the first and second maximum amount
```java
class Solution {
    public int fillCups(int[] amount) {
        int count = 0;
        int lastIndex = amount.length - 1;
        int lastSecondIndex = lastIndex - 1;

        Arrays.sort(amount);
        while (amount[lastIndex] != 0) {
            if (amount[lastSecondIndex] >= 1 && amount[lastIndex] >= 1) {
                amount[lastSecondIndex]--;
            }

            amount[lastIndex]--;
            count++;

            Arrays.sort(amount);
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 66.83%)
- Memory: 40.99 MB (Beats: 74.20%)

<br>
