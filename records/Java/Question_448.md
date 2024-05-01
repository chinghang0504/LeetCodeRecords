# [LeetCode Records](../../README.md) - Question 448 Find All Numbers Disappeared in an Array

### Attempt 1: Use a boolean array to record counts
```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        boolean[] saved = new boolean[nums.length + 1];

        for (int i = 0; i < nums.length; i++) {
            saved[nums[i]] = true;
        }

        List<Integer> result = new ArrayList<>();
        for (int i = 1; i < saved.length; i++) {
            if (!saved[i]) {
                result.add(i);
            }
        }

        return result;
    }
}
```
- Runtime: 3 ms (Beats: 99.35%)
- Memory: 55.15 MB (Beats: 25.91%)

<br>
