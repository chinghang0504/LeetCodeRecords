# [LeetCode Records](../../README.md) - Question 219 Contains Duplicate II

### Attempt 1: Check every neighbour
```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        for (int i = 0; i < nums.length; i++){
            int curr = nums[i];
            for (int j = i + 1; j <= i + k && j < nums.length; j++) {
                if (curr == nums[j]) {
                    return true;
                }
            }
        }

        return false;
    }
}
```
- Runtime: 976 ms (Beats: 9.01%)
- Memory: 55.00 MB (Beats: 89.06%)

<br>

### Attempt 2: Use a HashMap to record the previous index
```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();

        for (int i = 0; i < nums.length; i++){
            Integer index = hashMap.get(nums[i]);
            if (index == null) {
                hashMap.put(nums[i], i);
            } else {
                if (i - index <= k) {
                    return true;
                } else {
                    hashMap.put(nums[i], i);
                }
            }
        }

        return false;
    }
}
```
- Runtime: 18 ms (Beats: 80.18%)
- Memory: 58.30 MB (Beats: 7.54%)

<br>
