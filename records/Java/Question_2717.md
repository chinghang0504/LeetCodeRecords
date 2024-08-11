# [LeetCode Records](../../README.md) - Question 2717 Semi-Ordered Permutation

### Attempt 1: First the first and last indices
```java
class Solution {
    public int semiOrderedPermutation(int[] nums) {
        int n = nums.length;
        int firstIndex = -1;
        int lastIndex = -1;

        for (int i = 0; firstIndex == -1 || lastIndex == -1; i++) {
            if (nums[i] == 1) {
                firstIndex = i;
            } else if (nums[i] == n) {
                lastIndex = i;
            }
        }

        if (firstIndex < lastIndex) {
            return firstIndex + n - lastIndex - 1;
        } else {
            return firstIndex + n - lastIndex - 2;
        }
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.73 MB (Beats: 5.80%)

<br>
