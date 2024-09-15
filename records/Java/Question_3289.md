# [LeetCode Records](../../README.md) - Question 3289 The Two Sneaky Numbers of Digitville

### Attempt 1: Record the number counts
```java
class Solution {
    public int[] getSneakyNumbers(int[] nums) {
        int[] counts = new int[nums.length];

        for (int num : nums) {
            counts[num]++;
        }

        int[] ans = new int[2];
        int j = 0;
        for (int i = 0; i < nums.length; i++) {
            if (counts[i] == 2) {
                ans[j] = i;
                j++;

                if (j == 2) {
                    break;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.40 MB (Beats: 100.00%)

<br>
