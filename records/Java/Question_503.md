# [LeetCode Records](../../README.md) - Question 503 Next Greater Element II

### Attempt 1: Use two for loops to find the next greater number
```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int[] ans = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            boolean notFound = true;
            int currNum = nums[i];
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] > currNum) {
                    ans[i] = nums[j];
                    notFound = false;
                    break;
                }
            }
            if (notFound) {
                for (int j = 0; j < i; j++) {
                    if (nums[j] > currNum) {
                        ans[i] = nums[j];
                        notFound = false;
                        break;
                    }
                }
            }

            if (notFound) {
                ans[i] = -1;
            }
        }

        return ans;
    }
}
```
- Runtime: 30 ms (Beats: 16.50%)
- Memory: 45.96 MB (Beats: 71.73%)

<br>
