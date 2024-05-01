# [LeetCode Records](../../README.md) - Question 41 First Missing Positive

### Attempt 1: Use a HashSet
```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        HashSet<Integer> hashSet = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            hashSet.add(nums[i]);
        }

        int curr = 1;
        while (true) {
            if (!hashSet.contains(curr)) {
                break;
            }
            curr++;
        }

        return curr;
    }
}
```
- Runtime: 9 ms (Beats: 32.95%)
- Memory: 58.57 MB (Beats: 8.84%)

<br>

### Attempt 2: Use an array
```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int[] counts = new int[nums.length + 1];
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > 0 && nums[i] < counts.length) {
                counts[nums[i]] = 1;
            }
        }

        int i = 1;
        for (; i < counts.length; i++) {
            if (counts[i] != 1) {
                return i;
            }
        }

        return i;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 57.50 MB (Beats: 19.53%)

<br>
