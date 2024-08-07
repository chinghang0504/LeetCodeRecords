# [LeetCode Records](../../README.md) - Question 888 Fair Candy Swap

### Attempt 1: Use a nested loop to find box1 and box2 that can balance the totals of both
```java
class Solution {
    public int[] fairCandySwap(int[] aliceSizes, int[] bobSizes) {
        int aliceTotal = 0;
        int bobTotal = 0;

        for (int size : aliceSizes) {
            aliceTotal += size;
        }
        for (int size : bobSizes) {
            bobTotal += size;
        }

        for (int i = 0; i < aliceSizes.length; i++) {
            for (int j = 0; j < bobSizes.length; j++) {
                int box1 = aliceSizes[i];
                int box2 = bobSizes[j];

                if (aliceTotal - box1 + box2 == bobTotal - box2 + box1) {
                    return new int[]{ box1, box2 };
                }
            }
        }
        
        return null;
    }
}
```
- Runtime: 207 ms (Beats: 22.85%)
- Memory: 45.74 MB (Beats: 50.00%)

<br>
