# [LeetCode Records](../../README.md) - Question 860 Lemonade Change

### Attempt 1: Count the number of $5 and $10 Notes
```java
class Solution {
    public boolean lemonadeChange(int[] bills) {
        int[] cashCount = { 0, 0 };

        for (int i = 0; i < bills.length; i++) {
            if (bills[i] == 5) {
                cashCount[0]++;
            } else if (bills[i] == 10) {
                if (cashCount[0] > 0) {
                    cashCount[0]--;
                    cashCount[1]++;
                } else {
                    return false;
                }
            } else {
                if (cashCount[1] > 0 && cashCount[0] > 0) {
                    cashCount[1]--;
                    cashCount[0]--;
                } else if (cashCount[0] > 2) {
                    cashCount[0] -= 3;
                } else {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 95.75%)
- Memory: 55.69 MB (Beats: 69.70%)

<br>
