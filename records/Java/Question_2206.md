# [LeetCode Records](../../README.md) - Question 2206 Divide Array Into Equal Pairs

### Attempt 1: Use an int[] to reocrd the number counts
```java
class Solution {
    public boolean divideArray(int[] nums) {
        int[] counts = new int[501];

        for (int num : nums) {
            counts[num]++;
        }

        for (int i = 1; i < 501; i++) {
            if (counts[i] != 0 && counts[i] % 2 != 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.03 MB (Beats: 77.75%)

<br>
