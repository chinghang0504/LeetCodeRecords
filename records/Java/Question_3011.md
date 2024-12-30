# [LeetCode Records](../../README.md) - Question 3011 Find if Array Can Be Sorted

### Attempt 1: Use Arrays.sort() to sort each subarray
```java
class Solution {
    public boolean canSortArray(int[] nums) {
        int[] bitCounts = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            bitCounts[i] = Integer.bitCount(nums[i]);
        }

        int startIndex = 0;
        for (int i = 1; i < nums.length; i++) {
            if (bitCounts[startIndex] != bitCounts[i]) {
                Arrays.sort(nums, startIndex, i);
                startIndex = i;
            }
        }
        Arrays.sort(nums, startIndex, nums.length);

        for (int i = 1; i < nums.length; i++) {
            if (nums[i - 1] > nums[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 45.91%)
- Memory: 44.38 MB (Beats: 49.56%)

<br>

### Attempt 2: Compare the previous maximum with the current minimum of each subarray
```java
class Solution {
    public boolean canSortArray(int[] nums) {
        int[] bitCounts = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            bitCounts[i] = Integer.bitCount(nums[i]);
        }

        int prevMin = nums[0];
        int prevMax = nums[0];
        int startIndex = 0;
        for (int i = 1; i < nums.length; i++) {
            if (bitCounts[startIndex] != bitCounts[i]) {
                startIndex = i;
                break;
            } else {
                if (nums[i] > prevMax) {
                    prevMax = nums[i];
                } else if (nums[i] < prevMin) {
                    prevMin = nums[i];
                }
            }
        }
        if (startIndex == 0) {
            return true;
        }

        int currMin = nums[startIndex];
        int currMax = nums[startIndex];
        for (int i = startIndex + 1; i < nums.length; i++) {
            if (bitCounts[startIndex] != bitCounts[i]) {
                if (prevMax > currMin) {
                    return false;
                } else {
                    prevMin = currMin;
                    prevMax = currMax;
                    currMin = nums[i];
                    currMax = nums[i];
                    startIndex = i;
                }
            } else {
                if (nums[i] > currMax) {
                    currMax = nums[i];
                } else if (nums[i] < currMin) {
                    currMin = nums[i];
                }
            }
        }

        return prevMax <= currMin;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.31 MB (Beats: 49.56%)

<br>
