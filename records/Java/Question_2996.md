# [LeetCode Records](../../README.md) - Question 2996 Smallest Missing Integer Greater Than Sequential Prefix Sum

### Attempt 1: Use a HashSet to find the missing number
```java
class Solution {
    public int missingInteger(int[] nums) {
        int sum = nums[0];
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] == nums[i - 1] + 1) {
                sum += nums[i];
            } else {
                break;
            }
        }

        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        while (set.contains(sum)) {
            sum++;
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 91.29%)
- Memory: 42.51 MB (Beats: 12.36%)

<br>
