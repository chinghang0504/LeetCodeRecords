# [LeetCode Records](../../README.md) - Question 905 Sort Array By Parity

### Attempt 1: Run the first loop for the even numbers and the second loop for the odd numbers

```java
class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int[] result = new int[nums.length];

        int curr = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] % 2 == 0) {
                result[curr] = nums[i];
                curr++;
            }
        }
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] % 2 == 1) {
                result[curr] = nums[i];
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 58.06%)
- Memory: 44.43 MB (Beats: 89.26%)

<br>
