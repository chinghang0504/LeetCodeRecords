# [LeetCode Records](../../README.md) - Question 137 Single Number II

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);

        int curr = nums[0];
        int count = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != curr) {
                if (count != 3) {
                    return nums[i - 1];
                } else {
                    curr = nums[i];
                    count = 1;
                }
            } else {
                count++;
            }
        }

        return curr;
    }
}
```
- Runtime: 4 ms (Beats: 59.13%)
- Memory: 45.25 MB (Beats: 62.90%)

<br>
