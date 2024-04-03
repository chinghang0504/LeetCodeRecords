# [LeetCode Records](../README.md) - Question 217 Contains Duplicate

### Attempt 1: Use a HashSet
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> hashSet = new HashSet<>();

        for (int i = 0; i < nums.length; i++) {
            if (hashSet.contains(nums[i])) {
                return true;
            } else {
                hashSet.add(nums[i]);
            }
        }

        return false;
    }
}
```
- Runtime: 10 ms (Beats: 87.68%)
- Memory: 57.86 MB (Beats: 65.48%)

<br>
