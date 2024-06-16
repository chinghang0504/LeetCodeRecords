# [LeetCode Records](../../README.md) - Question 2824 Count Pairs Whose Sum is Less than Target

### Attempt 1: Use a nested loop
```java
class Solution {
    public int countPairs(List<Integer> nums, int target) {
        int count = 0;
        int size = nums.size();

        for (int i = 0; i < size - 1; i++) {
            for (int j = i + 1; j < size; j++) {
                if (nums.get(i) + nums.get(j) < target) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 96.86%)
- Memory: 42.37 MB (Beats: 28.62%)

<br>
