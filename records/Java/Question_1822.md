# [LeetCode Records](../../README.md) - Question 1822 Sign of the Product of an Array

### Attempt 1: Use a loop
```java
class Solution {
    public int arraySign(int[] nums) {
        int product = 1;

        for (int num : nums) {
            if (num > 0) {
                product *= 1;
            } else if (num < 0) {
                product *= -1;
            } else {
                product *= 0;
            }
        }

        return product;
    }
}
```
- Runtime: 1 ms (Beats: 22.68%)
- Memory: 43.92 MB (Beats: 40.47%)

<br>

### Attempt 2: Use a loop and break when the number is zero
```java
class Solution {
    public int arraySign(int[] nums) {
        int product = 1;

        for (int num : nums) {
            if (num > 0) {
                product *= 1;
            } else if (num < 0) {
                product *= -1;
            } else {
                product *= 0;
                break;
            }
        }

        return product;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.67 MB (Beats: 84.37%)

<br>
