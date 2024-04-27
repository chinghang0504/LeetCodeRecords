# [LeetCode Records](../README.md) - Question 575 Distribute Candies

### Attempt 1: Use a HashSet
```java
class Solution {
    public int distributeCandies(int[] candyType) {
        Set<Integer> set = new HashSet<>();

        for (int i = 0; i < candyType.length; i++) {
            set.add(candyType[i]);
        }

        int diffTypesNum = set.size();
        int maxCandiesNum = candyType.length / 2;

        return maxCandiesNum >= diffTypesNum ? diffTypesNum : maxCandiesNum;
    }
}
```
- Runtime: 30 ms (Beats: 81.25%)
- Memory: 45.95 MB (Beats: 23.86%)

<br>
