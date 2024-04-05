# [LeetCode Records](../README.md) - Question 268 Missing Number

### Attempt 1: Use a HashSet
```java
class Solution {
    public int missingNumber(int[] nums) {
        HashSet<Integer> hashSet = new HashSet<>();

        for (int i : nums) {
            hashSet.add(i);
        }

        for (int i = 0; i <= nums.length; i++) {
            if (!hashSet.contains(i)) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 5 ms (Beats: 27.35%)
- Memory: 45.51 MB (Beats: 11.95%)

<br>

### Attempt 2: Use a boolean array
```java
class Solution {
    public int missingNumber(int[] nums) {
        boolean[] arr = new boolean[nums.length + 1];

        for (int i : nums) {
            arr[i] = true;
        }

        for (int i = 0; i < nums.length + 1; i++) {
            if (!arr[i]) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.02 MB (Beats: 67.99%)

<br>
