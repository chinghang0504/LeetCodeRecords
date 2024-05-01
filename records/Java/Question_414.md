# [LeetCode Records](../../README.md) - Question 414 Third Maximum Number

### Attempt 1: Use a loop
```java
class Solution {
    public int thirdMax(int[] nums) {
        Integer n1 = null;
        Integer n2 = null;
        Integer n3 = null;

        for (int i = 0; i < nums.length; i++) {
            int target = nums[i];

            if (n1 == null || target > n1) {
                n3 = n2;
                n2 = n1;
                n1 = target;
            } else if (target == n1) {
                continue;
            } else if (n2 == null || target > n2) {
                n3 = n2;
                n2 = target;
            } else if (target == n2) {
                continue;
            } else if (n3 == null || target > n3) {
                n3 = target;
            }
        }

        if (nums.length >= 3) {
            return n3 != null ? n3 : n1;
        } else {
            return n1;
        }
    }
}
```
- Runtime: 2 ms (Beats: 78.16%)
- Memory: 43.25 MB (Beats: 39.13%)

<br>
