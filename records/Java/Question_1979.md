# [LeetCode Records](../../README.md) - Question 1979 Find Greatest Common Divisor of Array

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int findGCD(int[] nums) {
        Arrays.sort(nums);

        int smallest = nums[0];
        int largest = nums[nums.length - 1];

        for (int i = smallest; i > 1; i--) {
            if (smallest % i == 0 && largest % i == 0) {
                return i;
            }
        }

        return 1;
    }
}
```
- Runtime: 2 ms (Beats: 48.92%)
- Memory: 43.26 MB (Beats: 27.70%)

<br>

### Attempt 2: Find the min and max first
```java
class Solution {
    public int findGCD(int[] nums) {
        int min = nums[0];
        int max = nums[0];

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] < min) {
                min = nums[i];
            } else if (nums[i] > max) {
                max = nums[i];
            }
        }

        for (int i = min; i > 1; i--) {
            if (min % i == 0 && max % i == 0) {
                return i;
            }
        }

        return 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.07 MB (Beats: 55.09%)

<br>
