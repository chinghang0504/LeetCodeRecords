# [LeetCode Records](../../README.md) - Question 2089 Find Target Indices After Sorting Array

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public List<Integer> targetIndices(int[] nums, int target) {
        Arrays.sort(nums);

        List<Integer> result = new ArrayList<>();

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                result.add(i);
            } else if (nums[i] > target) {
                break;
            }
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 83.74%)
- Memory: 42.66 MB (Beats: 96.59%)

<br>
