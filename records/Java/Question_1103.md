# [LeetCode Records](../../README.md) - Question 1103 Distribute Candies to People

### Attempt 1: Loop until no candies
```java
class Solution {
    public int[] distributeCandies(int candies, int num_people) {
        int[] result = new int[num_people];

        int curr = 1;
        int i = 0;
        while (candies - curr >= 0) {
            result[i] += curr;
            candies -= curr;
            i++;
            curr++;

            if (i >= num_people) {
                i = 0;
            }
        }
        
        if (candies > 0) {
            result[i] += candies;
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 93.35%)
- Memory: 40.76 MB (Beats: 79.80%)

<br>
