# [LeetCode Records](../../README.md) - Question 1475 Final Prices With a Special Discount in a Shop

### Attempt 1: Clone the array first
```java
class Solution {
    public int[] finalPrices(int[] prices) {
        int[] answer = prices.clone();

        for (int i = 0; i < prices.length; i++) {
            for (int j = i + 1; j < prices.length; j++) {
                if (prices[i] >= prices[j]) {
                    answer[i] = prices[i] - prices[j];
                    break;
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 98.67%)
- Memory: 43.38 MB (Beats: 80.28%)

<br>
