# [LeetCode Records](../../README.md) - Question 1431 Kids With the Greatest Number of Candies

### Attempt 1: Find the max integer
```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int max = candies[0];
        for (int i = 1; i < candies.length; i++) {
            if (candies[i] > max) {
                max = candies[i];
            }
        }

        List<Boolean> result = new ArrayList<>();
        for (int i = 0; i < candies.length; i++) {
            result.add(candies[i] + extraCandies >= max);
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.19 MB (Beats: 62.89%)

<br>
