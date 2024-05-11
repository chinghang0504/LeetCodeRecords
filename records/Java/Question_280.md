# [LeetCode Records](../../README.md) - Question 280 Wiggle Sort

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public void wiggleSort(int[] nums) {
        int[] copy = nums.clone();
        Arrays.sort(copy);

        int currIndex = 0;
        int i = 0;
        for (; i < nums.length / 2; i++) {
            nums[currIndex] = copy[i];
            nums[currIndex + 1] = copy[nums.length - 1 - i];
            currIndex += 2;
        }
        if (nums.length % 2 == 1) {
            nums[currIndex] = copy[i];
        }
    }
}
```
- Runtime: 3 ms (Beats: 37.74%)
- Memory: 45.23 MB (Beats: 90.14%)

<br>
