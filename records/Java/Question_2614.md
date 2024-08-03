# [LeetCode Records](../../README.md) - Question 2614 Prime In Diagonal

### Attempt 1: Use a helper function to check if the number is prime
```java
class Solution {
    public int diagonalPrime(int[][] nums) {
        int n = nums.length;
        int[] values = new int[n * 2];
        int size = 0;

        for (int i = 0; i < n; i++) {
            values[size] = nums[i][i];
            size++;
        }
        for (int i = 0; i < n; i++) {
            values[size] = nums[i][n - i - 1];
            size++;
        }

        Arrays.sort(values);
        
        for (int i = values.length - 1; i >= 0; i--) {
            if (isPrime(values[i])) {
                return values[i];
            }
        }

        return 0;
    }

    private boolean isPrime(int num) {
        if (num == 1) {
            return false;
        }

        for (int i = 2; i < num / 2; i++) {
            if (num % i == 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 16 ms (Beats: 17.40%)
- Memory: 59.03 MB (Beats: 34.21%)

<br>
