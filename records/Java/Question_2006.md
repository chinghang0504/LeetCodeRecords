# [LeetCode Records](../../README.md) - Question 2006 Count Number of Pairs With Absolute Difference K

### Attempt 1: Use two loops and Math.abs()
```java
class Solution {
    public int countKDifference(int[] nums, int k) {
        int count = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (Math.abs(nums[i] - nums[j]) == k) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 7 ms (Beats: 57.05%)
- Memory: 43.36 MB (Beats: 49.98%)

<br>

### Attempt 2: Use two loops and Arrays.sort()
```java
class Solution {
    public int countKDifference(int[] nums, int k) {
        int count = 0;

        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] - nums[i] == k) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 5 ms (Beats: 73.41%)
- Memory: 43.31 MB (Beats: 49.98%)

<br>

### Attempt 3: Use two loops and Arrays.sort()
```java
class Solution {
    public int countKDifference(int[] nums, int k) {
        int count = 0;

        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 1; i++) {
            int target = k + nums[i];
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] == target) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 5 ms (Beats: 73.41%)
- Memory: 42.54 MB (Beats: 99.31%)

<br>
