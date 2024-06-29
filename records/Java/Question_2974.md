# [LeetCode Records](../../README.md) - Question 2974 Minimum Number Game

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public int[] numberGame(int[] nums) {
        Arrays.sort(nums);

        int[] arr = new int[nums.length];
        
        int i = 0;
        while (i < nums.length) {
            arr[i] = nums[i + 1];
            arr[i + 1] = nums[i];

            i += 2;
        }
        
        return arr;
    }
}
```
- Runtime: 2 ms (Beats: 97.38%)
- Memory: 45.06 MB (Beats: 8.13%)

<br>
