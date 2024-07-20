# [LeetCode Records](../../README.md) - Question 2229 Check if an Array Is Consecutive

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public boolean isConsecutive(int[] nums) {
        Arrays.sort(nums);

        int curr = nums[0] + 1;
        for (int i = 1; i < nums.length; i++, curr++) {
            if (nums[i] != curr) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 30 ms (Beats: 43.42%)
- Memory: 59.76 MB (Beats: 48.68%)

<br>

### Attempt 2: Use a HashSet and two loops
```java
class Solution {
    public boolean isConsecutive(int[] nums) {
        Set<Integer> set = new HashSet<>();
        int min = Integer.MAX_VALUE;

        for (int num : nums) {
            set.add(num);
            min = Math.min(min, num);
        }

        for (int i = 0; i < nums.length; i++) {
            if (!set.contains(min + i)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 25 ms (Beats: 72.37%)
- Memory: 58.46 MB (Beats: 78.95%)

<br>

### Attempt 3: Use a boolean[] and two loops
```java
class Solution {
    public boolean isConsecutive(int[] nums) {
        boolean[] saved = new boolean[100001];
        int min = Integer.MAX_VALUE;

        for (int num : nums) {
            saved[num] = true;
            min = Math.min(min, num);
        }

        for (int i = 0; i < nums.length; i++) {
            if (!saved[min + i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 4 ms (Beats: 96.05%)
- Memory: 56.93 MB (Beats: 96.05%)

<br>
