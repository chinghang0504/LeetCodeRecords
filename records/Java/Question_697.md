# [LeetCode Records](../../README.md) - Question 697 Degree of an Array

### Attempt 1: Use an int[] to save the number counts and a helper function to find the length of subarray
```java
class Solution {
    public int findShortestSubArray(int[] nums) {
        int[] counts = new int[50000];
        int maxCount = 0;

        for (int num : nums) {
            counts[num]++;
            maxCount = Math.max(maxCount, counts[num]);
        }

        List<Integer> maxCounts = new ArrayList<>();
        for (int i = 0; i < 50000; i++) {
            if (counts[i] == maxCount) {
                maxCounts.add(i);
            }
        }

        int minLength = Integer.MAX_VALUE;
        for (int target : maxCounts) {
            int length = getLength(nums, target);
            minLength = Math.min(minLength, length);
        }

        return minLength;
    }

    private int getLength(int[] nums, int target) {
        int firstIndex = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                firstIndex = i;
                break;
            }
        }

        int lastIndex = 0;
        for (int i = nums.length - 1; i >= 0; i--) {
            if (nums[i] == target) {
                lastIndex = i;
                break;
            }
        }

        return lastIndex - firstIndex + 1;
    }
}
```
- Runtime: 37 ms (Beats: 24.95%)
- Memory: 49.58 MB (Beats: 7.56%)

<br>
