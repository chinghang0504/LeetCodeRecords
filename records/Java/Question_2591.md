# [LeetCode Records](../../README.md) - Question 2591 Distribute Money to Maximum Children

### Attempt 1: Calculate the quotient and remainder
```java
class Solution {
    public int distMoney(int money, int children) {
        // Someone receives 0 dollar
        if (money < children) {
            return -1;
        }

        // Everyone has one dollar
        money -= children;
        int quotient = money / 7;
        int remainder = money % 7;
        
        // Everyone has 8 dollars
        if (quotient == children && remainder == 0) {
            return children;
        } 
        // Everyone has 8 dollars except one child
        else if (quotient >= children) {
            return children - 1;
        }
        // No one has 4 dollars
        else if (remainder + 1 != 4) {
            return quotient;
        }

        // Someone has 4 dolloars
        return quotient == children - 1 ? quotient - 1 : quotient;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.07 MB (Beats: 32.91%)

<br>
