# [LeetCode Records](../../README.md) - Question 2815 Max Pair Sum in an Array

### Attempt 1: Use an int[][] to save the numbers
```java
class Solution {
    public int maxSum(int[] nums) {
        int[][] saved = new int[10][nums.length];
        int[] sizes = new int[10];

        for (int num : nums) {
            int largestDigit = getLargestDigit(num);
            saved[largestDigit][sizes[largestDigit]] = num;
            sizes[largestDigit]++;
        }

        int max = -1;
        for (int i = 0; i < 10; i++) {
            if (sizes[i] >= 2) {
                int size = sizes[i];
                Arrays.sort(saved[i], 0, size);
                max = Math.max(max, saved[i][size - 2] + saved[i][size - 1]);
            }
        }

        return max;
    }

    private int getLargestDigit(int num) {
        boolean[] digits = new boolean[10];

        while (num > 0) {
            digits[num % 10] = true;
            num /= 10;
        }

        for (int i = 9; i >= 0; i--) {
            if (digits[i]) {
                return i;
            }
        }

        return 0;
    }
}
```
- Runtime: 6 ms (Beats: 65.37%)
- Memory: 44.54 MB (Beats: 45.89%)

<br>
