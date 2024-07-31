# [LeetCode Records](../../README.md) - Question 976 Largest Perimeter Triangle

### Attempt 1: Use Arrays.sort() to sort the length first
```java
class Solution {
    public int largestPerimeter(int[] nums) {
        Arrays.sort(nums);

        for (int i = nums.length - 1; i >= 2; i--) {
            for (int j = i - 1; j >= 1; j--) {
                for (int k = j - 1; k >= 0; k--) {
                    if (canFormTriangle(nums[i], nums[j], nums[k])) {
                        return nums[i] + nums[j] + nums[k];
                    } else {
                        break;
                    }
                }
            }
        }

        return 0;
    }

    private boolean canFormTriangle(int a, int b, int c) {
        return (a + b > c) && (b + c > a) && (c + a > b);
    }
}
```
- Runtime: 12 ms (Beats: 14.40%)
- Memory: 44.67 MB (Beats: 87.06%)

<br>
