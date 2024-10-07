# [LeetCode Records](../../README.md) - Question 238 Product of Array Except Self

### Attempt 1: Count the number of zeros
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int totalProduct = 1;
        int zeroCount = 0;
        for (int num : nums) {
            if (num != 0) {
                totalProduct *= num;
            } else {
                zeroCount++;
            }
        }

        int[] ans = new int[nums.length];
        if (zeroCount >= 2) {
            return ans;
        }

        if (zeroCount == 0) {
            for (int i = 0; i < nums.length; i++) {
                ans[i] = totalProduct / nums[i];
            }
        } else {
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] == 0) {
                    ans[i] = totalProduct;
                    break;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 88.65%)
- Memory: 55.06 MB (Beats: 88.13%)

<br>
