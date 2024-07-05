# [LeetCode Records](../../README.md) - Question 2848 Points That Intersect With Cars

### Attempt 1: Use an boolean[] to record the numbers
```java
class Solution {
    public int numberOfPoints(List<List<Integer>> nums) {
        boolean[] covered = new boolean[101];

        for (List<Integer> list : nums) {
            for (int i = list.get(0); i <= list.get(1); i++) {
                covered[i] = true;
            }
        }

        int count = 0;
        for (int i = 1; i < 101; i++) {
            if (covered[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 85.35%)
- Memory: 44.58 MB (Beats: 17.04%)

<br>
