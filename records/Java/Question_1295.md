# [LeetCode Records](../../README.md) - Question 1295 Find Numbers with Even Number of Digits

### Attempt 1: Use a helper function
```java
class Solution {
    public int findNumbers(int[] nums) {
        int sum = 0;
        
        for (int num : nums) {
            if (isEvenNumberofDigits(num)) {
                sum++;
            }
        }

        return sum;
    }

    private boolean isEvenNumberofDigits(int num) {
        if (num <= 9) {
            return false;
        } else if (num <= 99) {
            return true;
        } else if (num <= 999) {
            return false;
        } else if (num <= 9999) {
            return true;
        } else if (num <= 99999) {
            return false;
        } else {
            return true;
        }
    }
}
```
- Runtime: 1 ms (Beats: 99.00%)
- Memory: 42.95 MB (Beats: 32.14%)

<br>
