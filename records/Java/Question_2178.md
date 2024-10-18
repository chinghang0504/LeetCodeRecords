# [LeetCode Records](../../README.md) - Question 2178 Maximum Split of Positive Even Integers

### Attempt 1: Increase the factor by 2 in each loop
```java
class Solution {
    public List<Long> maximumEvenSplit(long finalSum) {
        List<Long> ans = new ArrayList<>();

        if (finalSum % 2 == 1) {
            return ans;
        }

        long factor = 2;
        while (finalSum >= factor) {
            ans.add(factor);
            finalSum -= factor;
            factor += 2;
        }
        ans.add(ans.removeLast() + finalSum);
        
        return ans;
    }
}
```
- Runtime: 9 ms (Beats: 100.00%)
- Memory: 60.94 MB (Beats: 87.98%)

<br>
