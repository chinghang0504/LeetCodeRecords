# [LeetCode Records](../../README.md) - Question 2148 Count Elements With Strictly Smaller and Greater Elements

### Attempt 1: Use Array.sort() and a for loop
```java
class Solution {
    public int countElements(int[] nums) {
        Arrays.sort(nums);

        int min = nums[0];
        int max = nums[nums.length - 1];

        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != min && nums[i] != max) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 63.74%)
- Memory: 41.39 MB (Beats: 88.11%)

<br>

### Attempt 2: Use two for loops
```java
class Solution {
    public int countElements(int[] nums) {
        int min = nums[0];
        int max = nums[0];

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > max) {
                max = nums[i];
            } else if (nums[i] < min) {
                min = nums[i];
            }
        }

        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != min && nums[i] != max) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.69 MB (Beats: 50.10%)

<br>
