# [LeetCode Records](../../README.md) - Question 1004 Max Consecutive Ones III

### Attempt 1: Use a LinkedList to store the zero indices
```java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int maxLen = k;

        int currLen = 0;
        if (k == 0) {
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] == 1) {
                    currLen++;
                    maxLen = Math.max(maxLen, currLen);
                } else {
                    currLen = 0;
                }
            }
        } else {
            List<Integer> zeroIndexList = new LinkedList<>();
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] == 1) {
                    currLen++;
                    maxLen = Math.max(maxLen, currLen);
                } else if (zeroIndexList.size() < k) {
                    currLen++;
                    maxLen = Math.max(maxLen, currLen);
                    zeroIndexList.addLast(i);
                } else {
                    currLen = i - zeroIndexList.removeFirst();
                    zeroIndexList.addLast(i);
                }
            }
        }

        return maxLen;
    }
}
```
- Runtime: 9 ms (Beats: 7.68%)
- Memory: 48.02 MB (Beats: 6.53%)

<br>

### Attempt 2: Use an int[] to store the zero indices
```java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int maxLen = k;

        int currLen = 0;
        if (k == 0) {
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] == 1) {
                    currLen++;
                    maxLen = Math.max(maxLen, currLen);
                } else {
                    currLen = 0;
                }
            }
        } else {
            int firstZeroIndex = 0;
            int[] zeroIndexArr = new int[nums.length];
            int zeroSize = 0;
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] == 1) {
                    currLen++;
                    maxLen = Math.max(maxLen, currLen);
                } else if (zeroSize - firstZeroIndex < k) {
                    currLen++;
                    maxLen = Math.max(maxLen, currLen);
                    zeroIndexArr[zeroSize] = i;
                    zeroSize++;
                } else {
                    currLen = i - zeroIndexArr[firstZeroIndex];
                    firstZeroIndex++;
                    zeroIndexArr[zeroSize] = i;
                    zeroSize++;
                }
            }
        }

        return maxLen;
    }
}
```
- Runtime: 4 ms (Beats: 26.73%)
- Memory: 47.53 MB (Beats: 6.53%)

<br>
