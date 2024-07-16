# [LeetCode Records](../../README.md) - Question 1196 How Many Apples Can You Put into the Basket

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public int maxNumberOfApples(int[] weight) {
        Arrays.sort(weight);

        int totalWeight = 0;
        int i = 0;
        while (i < weight.length) {
            int nextTotalWeight = totalWeight + weight[i];
            if (nextTotalWeight > 5000) {
                return i;
            } else {
                totalWeight = nextTotalWeight;
                i++;
            }
        }
        
        return weight.length;
    }
}
```
- Runtime: 4 ms (Beats: 97.07%)
- Memory: 43.80 MB (Beats: 97.72%)

<br>
