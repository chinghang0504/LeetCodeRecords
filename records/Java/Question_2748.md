# [LeetCode Records](../../README.md) - Question 2748 Number of Beautiful Pairs

### Attempt 1: Use a nested loop to test every case
```java
class Solution {
    public int countBeautifulPairs(int[] nums) {
        int count = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            int digit1 = getFirstDigit(nums[i]);
            for (int j = i + 1; j < nums.length; j++) {
                int digit2 = nums[j] % 10;

                if (isCoprime(digit1, digit2)) {
                    count++;
                }
            }
        }

        return count;
    }

    private int getFirstDigit(int num) {
        int digit = 0;

        while (num > 0) {
            digit = num % 10;
            num /= 10;
        }

        return digit;
    }

    private boolean isCoprime(int digit1, int digit2) {
        int min = Math.min(digit1, digit2);

        for (int i = 2; i <= min; i++) {
            if (digit1 % i == 0 && digit2 % i == 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 13 ms (Beats: 82.12%)
- Memory: 44.10 MB (Beats: 92.42%)

<br>
