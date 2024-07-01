# [LeetCode Records](../../README.md) - Question 3005 Count Elements With Maximum Frequency

### Attempt 1: Use a int[] to save the number counts
```java
class Solution {
    public int maxFrequencyElements(int[] nums) {
        int[] counts = new int[101];

        for (int num : nums) {
            counts[num]++;
        }

        int max = 0;
        int sum = 0;
        for (int count : counts) {
            if (count > max) {
                max = count;
                sum = count;
            } else if (count == max) {
                sum += count;
            }
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 99.65%)
- Memory: 42.17 MB (Beats: 44.62%)

<br>
