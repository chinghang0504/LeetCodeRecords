# [LeetCode Records](../../README.md) - Question 26 Remove Duplicates from Sorted Array

### Attempt 1: Check the last number
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int lastNum = nums[0];
        int currIndex = 1;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != lastNum) {
                lastNum = nums[i];
                nums[currIndex++] = lastNum;
            }
        }

        return currIndex;
    }
}
```
- Runtime: 1 ms (Beats: 74.62%)
- Memory: 44.55 MB (Beats: 73.31%)

<br>

### Attempt 2: Only track one variable
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int currIndex = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i - 1] != nums[i]) {
                nums[currIndex] = nums[i];
                currIndex++;
            }
        }

        return currIndex;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.13 MB (Beats: 7.59%)

<br>
