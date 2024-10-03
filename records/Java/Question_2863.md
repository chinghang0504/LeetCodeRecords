# [LeetCode Records](../../README.md) - Question 2863 Maximum Length of Semi-Decreasing Subarrays

### Attempt 1: Use Arrays.sort() to sort the array first
```java
class Solution {
    public int maxSubarrayLength(int[] nums) {
        int[][] arr = new int[nums.length][2];
        for (int i = 0; i < nums.length; i++) {
            arr[i][0] = nums[i];
            arr[i][1] = i;
        }

        Arrays.sort(arr, (numArr1, numArr2) -> {
            if (numArr1[0] != numArr2[0]) {
                return numArr2[0] - numArr1[0];
            }
            return numArr2[1] - numArr1[1];
        });

        int maxLength = 0;
        int currMinIndex = arr[0][1];
        for (int i = 1; i < arr.length; i++) {
            maxLength = Math.max(maxLength, arr[i][1] - currMinIndex + 1);
            currMinIndex = Math.min(currMinIndex, arr[i][1]);
        }

        return maxLength;
    }
}
```
- Runtime: 86 ms (Beats: 11.11%)
- Memory: 57.37 MB (Beats: 20.83%)

<br>
