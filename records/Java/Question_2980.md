# [LeetCode Records](../../README.md) - Question 2980 Check if Bitwise OR Has Trailing Zeros

### Attempt 1: Count the number of even numbers
```java
class Solution {
    public boolean hasTrailingZeros(int[] nums) {
        int count = 0;

        for (int num : nums) {
            if (num % 2 == 0) {
                count++;

                if (count >= 2) {
                    return true;
                }
            }
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 63.57%)
- Memory: 44.06 MB (Beats: 48.11%)

<br>
