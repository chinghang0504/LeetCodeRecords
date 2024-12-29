# [LeetCode Records](../../README.md) - Question 2966 Divide Array Into Arrays With Max Difference

### Attempt 1: Use Arrays.sort() to sort the array and compare the first and the last number in each subarray
```java
class Solution {
    public int[][] divideArray(int[] nums, int k) {
        Arrays.sort(nums);

        int rows = nums.length / 3;
        int[][] ans = new int[rows][3];
        for (int i = 0, j = 0; i < rows; i++, j += 3) {
            if (nums[j + 2] - nums[j] > k) {
                return new int[][]{};
            }

            ans[i][0] = nums[j];
            ans[i][1] = nums[j + 1];
            ans[i][2] = nums[j + 2];
        }

        return ans;
    }
}
```
- Runtime: 22 ms (Beats: 92.07%)
- Memory: 59.59 MB (Beats: 46.74%)

<br>
