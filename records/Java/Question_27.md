# [LeetCode Records](../../README.md) - Question 27 Remove Element 

### Attempt 1: Follow the current index
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int curr = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[curr++] = nums[i];
            }
        }

        return curr;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.28 MB (Beats: 8.81%)

<br>
