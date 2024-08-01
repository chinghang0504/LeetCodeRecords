# [LeetCode Records](../../README.md) - Question 2806 Account Balance After Rounded Purchase

### Attempt 1: Find the last digit first
```java
class Solution {
    public int accountBalanceAfterPurchase(int purchaseAmount) {
        int lastDigit = purchaseAmount % 10;
        if (lastDigit >= 5) {
            purchaseAmount = purchaseAmount + 10 - lastDigit;
        } else {
            purchaseAmount -= lastDigit;
        }

        return 100 - purchaseAmount;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.52 MB (Beats: 16.81%)

<br>
