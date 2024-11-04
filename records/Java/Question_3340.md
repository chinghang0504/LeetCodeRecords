# [LeetCode Records](../../README.md) - Question 3340 Check Balanced String

### Attempt 1: Compare the odd sum and the even sum
```java
class Solution {
    public boolean isBalanced(String num) {
        char[] arr = num.toCharArray();
        int evenSum = 0;
        int oddSum = 0;
        
        for (int i = 0; i < arr.length; i++) {
            if (i % 2 == 0) {
                evenSum += arr[i] - '0';
            } else {
                oddSum += arr[i] - '0';
            }
        }

        return evenSum == oddSum;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.98 MB (Beats: 100.00%)

<br>
