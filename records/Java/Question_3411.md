# [LeetCode Records](../../README.md) - Question 3411 Maximum Subarray With Equal Products

### Attempt 1: Test every case
```java
class Solution {
    public int maxLength(int[] nums) {
        int[][] primeFactors = new int[nums.length][];
        for (int i = 0; i < nums.length; i++) {
            primeFactors[i] = getPrimeFactor(nums[i]);
        }

        for (int i = nums.length; i >= 1; i--) {
            for (int j = 0; j < nums.length - i + 1; j++) {
                if (isProductEquivalent(primeFactors, nums, j, j + i)) {
                    return i;
                }
            }
        }

        return 0;
    }

    private int[] getPrimeFactor(int num) {
        switch (num) {
            case 2:
                return new int[] { 1, 0, 0, 0 };
            case 3:
                return new int[] { 0, 1, 0, 0 };
            case 4:
                return new int[] { 2, 0, 0, 0 };
            case 5:
                return new int[] { 0, 0, 1, 0 };
            case 6:
                return new int[] { 1, 1, 0, 0 };
            case 7:
                return new int[] { 0, 0, 0, 1 };
            case 8:
                return new int[] { 3, 0, 0, 0 };
            case 9:
                return new int[] { 0, 2, 0, 0 };
            case 10:
                return new int[] { 1, 0, 1, 0 };
        }

        return new int[] { 0, 0, 0, 0 };
    }

    private boolean isProductEquivalent(int[][] primeFactors, int[] nums, int start, int end) {
        int product = nums[start];
        int[] minPrimeFactor = Arrays.copyOf(primeFactors[start], 4);
        int[] maxPrimeFactor = Arrays.copyOf(primeFactors[start], 4);

        for (int i = start + 1; i < end; i++) {
            product *= nums[i];
            
            for (int j = 0; j < 4; j++) {
                minPrimeFactor[j] = Math.min(minPrimeFactor[j], primeFactors[i][j]);
                maxPrimeFactor[j] = Math.max(maxPrimeFactor[j], primeFactors[i][j]);
            }
        }

        int[] primeFactorValues = new int[]{ 2, 3, 5, 7 };
        int lcm = 1;
        int gcd = 1;
        for (int i = 0; i < 4; i++) {
            for (int j = 0; j < maxPrimeFactor[i]; j++) {
                lcm *= primeFactorValues[i];
            }
            for (int j = 0; j < minPrimeFactor[i]; j++) {
                gcd *= primeFactorValues[i];
            }
        }

        return product == lcm * gcd;
    }
}
```
- Runtime: 65 ms (Beats: -%)
- Memory: 44.93 MB (Beats: -%)

<br>
