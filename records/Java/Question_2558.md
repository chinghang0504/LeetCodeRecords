# [LeetCode Records](../../README.md) - Question 2558 Take Gifts From the Richest Pile

### Attempt 1: Find the maximum value in each loop
```java
class Solution {
    public long pickGifts(int[] gifts, int k) {
        for (int i = 0; i < k; i++) {
            int max = gifts[0];
            int maxIndex = 0;

            for (int j = 1; j < gifts.length; j++) {
                if (gifts[j] > max) {
                    max = gifts[j];
                    maxIndex = j;
                }
            }

            gifts[maxIndex] = (int)Math.sqrt(gifts[maxIndex]);
        }

        long sum = 0;
        for (int gift : gifts) {
            sum += gift;
        }

        return sum;
    }
}
```
- Runtime: 6 ms (Beats: 76.41%)
- Memory: 42.06 MB (Beats: 80.17%)

<br>
