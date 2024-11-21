# [LeetCode Records](../../README.md) - Question 2240 

### Attempt 1: Count every case
```java
class Solution {
    public long waysToBuyPensPencils(int total, int cost1, int cost2) {
        long count = 0;
        int maxNumOfItem1 = total / cost1;

        int remainder = total;
        for (int i = 0; i <= maxNumOfItem1; i++) {
            count += remainder / cost2 + 1;
            remainder -= cost1;
        }

        return count;
    }
}
```
- Runtime: 10 ms (Beats: 91.89%)
- Memory: 40.05 MB (Beats: 95.80%)

<br>
