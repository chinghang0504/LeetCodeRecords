# [LeetCode Records](../../README.md) - Question 3285 Find Indices of Stable Mountains

### Attempt 1: Check the previous height
```java
class Solution {
    public List<Integer> stableMountains(int[] height, int threshold) {
        List<Integer> ans = new ArrayList<>();

        for (int i = 1; i < height.length; i++) {
            if (height[i - 1] > threshold) {
                ans.add(i);
            }
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.56 MB (Beats: 100.00%)

<br>
