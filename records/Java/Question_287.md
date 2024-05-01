# [LeetCode Records](../../README.md) - Question 287 Find the Duplicate Number

### Attempt 1: Use a HashSet
```java
class Solution {
    public int findDuplicate(int[] nums) {
        HashSet<Integer> hashSet = new HashSet<>();

        for (int i = 0; i < nums.length; i++) {
            if (hashSet.contains(nums[i])) {
                return nums[i];
            } else {
                hashSet.add(nums[i]);
            }
        }

        return -1;
    }
}
```
- Runtime: 22 ms (Beats: 26.67%)
- Memory: 56.46 MB (Beats: 91.03%)

<br>

### Attempt 2: Use a boolean array
```java
class Solution {
    public int findDuplicate(int[] nums) {
        boolean[] saved = new boolean[nums.length + 1];

        for (int num : nums) {
            if (saved[num]) {
                return num;
            } else {
                saved[num] = true;
            }
        }
        
        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 58.16 MB (Beats: 50.44%)

<br>
