# [LeetCode Records](../../README.md) - Question 2011 Final Value of Variable After Performing Operations

### Attempt 1: Check the 2nd character
```java
class Solution {
    public int finalValueAfterOperations(String[] operations) {
        int sum = 0;

        for (String operation : operations) {
            sum += operation.charAt(1) == '+' ? 1 : -1;
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.57 MB (Beats: 49.08%)

<br>
