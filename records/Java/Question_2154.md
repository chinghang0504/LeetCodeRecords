# [LeetCode Records](../../README.md) - Question 2154 Keep Multiplying Found Values by Two

### Attempt 1: Use a HashSet, a for loop, and a while loop
```java
class Solution {
    public int findFinalValue(int[] nums, int original) {
        Set<Integer> set = new HashSet<>();

        for (int num : nums) {
            set.add(num);
        }

        while (set.contains(original)) {
            original *= 2;
        }

        return original;
    }
}
```
- Runtime: 3 ms (Beats: 67.17%)
- Memory: 44.30 MB (Beats: 14.55%)

<br>
