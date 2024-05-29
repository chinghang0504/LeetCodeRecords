# [LeetCode Records](../../README.md) - Question 1437 Check If All 1's Are at Least Length K Places Away

### Attempt 1: Record the last index of 1
```java
class Solution {
    public boolean kLengthApart(int[] nums, int k) {
        int prevIndex = nums.length;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1) {
                prevIndex = i;
                break;
            }
        }

        for (int i = prevIndex + 1; i < nums.length; i++) {
            if (nums[i] == 1) {
                if (i - prevIndex <= k) {
                    return false;
                }
                prevIndex = i;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 56.55 MB (Beats: 37.27%)

<br>
