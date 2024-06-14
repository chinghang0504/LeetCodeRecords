# [LeetCode Records](../../README.md) - Question 2441 Largest Positive Integer That Exists With Its Negative

### Attempt 1: Use a HashSet and Arrays.sort()
```java
class Solution {
    public int findMaxK(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        Arrays.sort(nums);
        
        for (int i = nums.length - 1; i >= 0; i--) {
            if (nums[i] > 0) {
                if (set.contains(-nums[i])) {
                    return nums[i];
                }
            } else {
                break;
            }
        }

        return -1;
    }
}
```
- Runtime: 8 ms (Beats: 17.71%)
- Memory: 45.14 MB (Beats: 10.02%)

<br>
