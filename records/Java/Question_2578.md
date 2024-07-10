# [LeetCode Records](../../README.md) - Question 2578 Split With Minimum Sum

### Attempt 1: Use an int[] to record the digits and Arrays.sort()
```java
class Solution {
    public int splitNum(int num) {
        int[] digits = new int[10];
        int size = 0;

        while (num > 0) {
            digits[size] = num % 10;
            num /= 10;
            size++;
        }

        Arrays.sort(digits, 0, size);

        int num1 = 0;
        int num2 = 0;
        for (int i = 0; i < size; i++) {
            if (i % 2 == 0) {
                num1 = num1 * 10 + digits[i];
            } else {
                num2 = num2 * 10 + digits[i];
            }
        }

        return num1 + num2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.23 MB (Beats: 70.77%)

<br>
