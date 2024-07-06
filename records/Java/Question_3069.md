# [LeetCode Records](../../README.md) - Question 3069 Distribute Elements Into Two Arrays I

### Attempt 1: Use an int[] to be the second array
```java
class Solution {
    public int[] resultArray(int[] nums) {
        int[] arr = new int[nums.length];
        int arrSize1 = 1;
        int arrSize2 = 1;
        arr[0] = nums[1];
        
        for (int i = 2; i < nums.length; i++) {
            if (nums[arrSize1 - 1] > arr[arrSize2 - 1]) {
                nums[arrSize1] = nums[i];
                arrSize1++;
            } else {
                arr[arrSize2] = nums[i];
                arrSize2++;
            }
        }

        for (int i = 0; i < arrSize2; i++) {
            nums[arrSize1 + i] = arr[i];
        }

        return nums;
    }
}
```
- Runtime: 1 ms (Beats: 99.66%)
- Memory: 44.65 MB (Beats: 42.11%)

<br>
