# [LeetCode Records](../../README.md) - Question 80 Remove Duplicates from Sorted Array II

### Attempt 1: Use an int[] to record the number counts
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int[] counts = new int[100000];
        int count = 0;
        int leftIndex = 0;

        for (int num : nums) {
            counts[num + 10000]++;
            if (counts[num + 10000] <= 2) {
                nums[leftIndex] = num;
                leftIndex++;
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 7.78%)
- Memory: 45.10 MB (Beats: 5.54%)

<br>
