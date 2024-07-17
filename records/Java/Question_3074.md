# [LeetCode Records](../../README.md) - Question 3074 Apple Redistribution into Boxes

### Attempt 1: Use two loops and Arrays.sort()
```java
class Solution {
    public int minimumBoxes(int[] apple, int[] capacity) {
        int totalApple = 0;
        for (int num : apple) {
            totalApple += num;
        }

        Arrays.sort(capacity);

        int i = capacity.length - 1;
        while (totalApple > 0 && i >= 0) {
            int nextTotalApple = totalApple - capacity[i];
            if (nextTotalApple <= 0) {
                return capacity.length - i;
            } else {
                totalApple = nextTotalApple;
                i--;
            }
        }

        return capacity.length;
    }
}
```
- Runtime: 1 ms (Beats: 99.73%)
- Memory: 41.82 MB (Beats: 87.40%)

<br>
