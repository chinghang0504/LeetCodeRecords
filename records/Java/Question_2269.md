# [LeetCode Records](../../README.md) - Question 2269 Find the K-Beauty of a Number

### Attempt 1: Use an int[] to save digits
```java
class Solution {
    public int divisorSubstrings(int num, int k) {
        int[] digits = new int[10];
        int size = 0;

        int n = num;
        while (n > 0) {
            digits[size] = n % 10;
            n /= 10;
            size++;
        }

        int count = 0;
        for (int i = size - 1; i >= k - 1; i--) {
            int sum = 0;
            for (int j = 0; j < k; j++) {
                sum = sum * 10 + digits[i - j];
            }

            if (sum == 0) {
                continue;
            } else if (num % sum == 0) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.66 MB (Beats: 23.97%)

<br>
