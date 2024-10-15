# [LeetCode Records](../../README.md) - Question 1291 Sequential Digits

### Attempt 1: Generate every possible case
```java
class Solution {
    public List<Integer> sequentialDigits(int low, int high) {
        int start = countSize(low);
        int end = countSize(high);
        List<Integer> ans = new ArrayList<>();

        for (int i = start; i <= end; i++) {
            getSequentialDigits(ans, i, low, high);
        }

        return ans;
    }

    private int countSize(int num) {
        int count = 0;
        while (num > 0) {
            num /= 10;
            count++;
        }
        return count;
    }

    private int digitsToNumber(int[] digits) {
        int num = 0;
        for (int i = 0; i < digits.length; i++) {
            num = num * 10 + digits[i];
        }
        return num;
    }

    private void getSequentialDigits(List<Integer> ans, int n, int low, int high) {
        int[] digits = new int[n];
        for (int i = 0; i < n; i++) {
            digits[i] = i + 1;
        }

        while (digits[n - 1] < 10) {
            int num = digitsToNumber(digits);
            if (num >= low) {
                if (num > high) {
                    break;
                } else {
                    ans.add(num);
                }
            }

            for (int i = 0; i < n; i++) {
                digits[i]++;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.78 MB (Beats: 65.59%)

<br>
