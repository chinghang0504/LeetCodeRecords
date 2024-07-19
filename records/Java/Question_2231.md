# [LeetCode Records](../../README.md) - Question 2231 Largest Number After Digit Swaps by Parity

### Attempt 1: Use two int[] to record the digits and the digit counts
```java
class Solution {
    public int largestInteger(int num) {
        int[] counts = new int[10];
        int[] digits = new int[10];
        int size = 0;

        while (num > 0) {
            int digit = num % 10;
            counts[digit]++;
            digits[size] = digit;
            size++;
            num /= 10;
        }

        int answer = 0;
        for (int i = size - 1; i >= 0; i--) {
            if (digits[i] % 2 == 1) {
                for (int j = 9; j >= 0; j -= 2) {
                    if (counts[j] > 0) {
                        counts[j]--;
                        answer = answer * 10 + j;
                        break;
                    }
                }
            } else {
                for (int j = 8; j >= 0; j -= 2) {
                    if (counts[j] > 0) {
                        counts[j]--;
                        answer = answer * 10 + j;
                        break;
                    }
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.46 MB (Beats: 58.09%)

<br>
