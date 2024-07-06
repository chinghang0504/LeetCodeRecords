# [LeetCode Records](../../README.md) - Question 2357 Make Array Zero by Subtracting Equal Amounts

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public int minimumOperations(int[] nums) {
        Arrays.sort(nums);

        int count = 0;
        int minIndex = 0;
        while (nums[nums.length - 1] != 0) {
            int min = nums[minIndex];
            if (min != 0) {
                for (int i = minIndex; i < nums.length; i++) {
                    nums[i] -= min;
                }
                count++;
            }

            minIndex++;
        }
        
        return count;
    }
}
```
- Runtime: 2 ms (Beats: 28.18%)
- Memory: 41.17 MB (Beats: 41.77%)

<br>

### Attempt 2: Use a boolean[] to record the numbers
```java
class Solution {
    public int minimumOperations(int[] nums) {
        boolean[] records = new boolean[101];

        for (int num : nums) {
            records[num] = true;
        }

        int count = 0;
        for (int i = 1; i < 101; i++) {
            if (records[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.00 MB (Beats: 70.73%)

<br>
