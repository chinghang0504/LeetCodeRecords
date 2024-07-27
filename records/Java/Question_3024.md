# [LeetCode Records](../../README.md) - Question 3024 Type of Triangle

### Attempt 1: Use a helper function to check if it is a triangle
```java
class Solution {
    public String triangleType(int[] nums) {
        int a = nums[0];
        int b = nums[1];
        int c = nums[2];

        if (!isTriangle(a, b, c)) {
            return "none";
        }

        if (a == b && a == c) {
            return "equilateral";
        } else if (a == b || b == c || a == c) {
            return "isosceles";
        } else {
            return "scalene";
        }
    }

    private boolean isTriangle(int a, int b, int c) {
        return a + b > c && b + c > a && c + a > b;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.62 MB (Beats: 80.95%)

<br>
