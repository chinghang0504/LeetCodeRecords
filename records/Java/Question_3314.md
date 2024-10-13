# [LeetCode Records](../../README.md) - Question 3314 Construct the Minimum Bitwise Array I

### Attempt 1: Test every possible case
```java
class Solution {
    public int[] minBitwiseArray(List<Integer> nums) {
        int size = nums.size();
        int[] ans = new int[size];

        int i = 0;
        for (int num : nums) {
            ans[i] = -1;
            for (int j = 0; j <= num - 1; j++) {
                if ((j | (j + 1)) == num) {
                    ans[i] = j;
                    break;
                }
            }

            i++;
        }

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.73 MB (Beats: 100.00%)

<br>
