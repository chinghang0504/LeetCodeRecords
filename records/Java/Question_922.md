# [LeetCode Records](../../README.md) - Question 922 Sort Array By Parity II

### Attempt 1: Use two variables to record the current index of even and odd numbers
```java
class Solution {
    public int[] sortArrayByParityII(int[] nums) {
        int[] result = new int[nums.length];
        int evenIndex = 0;
        int oddIndex = 1;

        for (int num : nums) {
            if (num % 2 == 0) {
                result[evenIndex] = num;
                evenIndex += 2;
            } else {
                result[oddIndex] = num;
                oddIndex += 2;
            }
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 99.47%)
- Memory: 46.34 MB (Beats: 90.07%)

<br>
