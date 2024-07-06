# [LeetCode Records](../../README.md) - Question 2843 Count Symmetric Integers

### Attempt 1: Use a help function to test each number
```java
class Solution {
    public int countSymmetricIntegers(int low, int high) {
        int count = 0;

        for (int i = low; i <= high; i++) {
            if (isSymmetricInteger(i)) {
                count++;
            }
        }

        return count;
    }

    private boolean isSymmetricInteger(int num) {
        int[] digits = new int[5];
        int size = 0;

        while (num > 0) {
            digits[size] = num % 10;
            num /= 10;
            size++;
        }

        if (size % 2 != 0) {
            return false;
        }

        int n = size / 2;
        int leftSum = 0;
        int rightSum = 0;
        for (int i = 0; i < n; i++) {
            rightSum += digits[i];
        }
        for (int i = n; i < size; i++) {
            leftSum += digits[i];
        }

        return leftSum == rightSum;
    }
}
```
- Runtime: 21 ms (Beats: 88.98%)
- Memory: 44.40 MB (Beats: 41.78%)

<br>
