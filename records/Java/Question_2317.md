# [LeetCode Records](../../README.md) - Question 2317 Maximum XOR After Operations

### Attempt 1: Use bitwise OR operator
```java
class Solution {
    public int maximumXOR(int[] nums) {
        int val = 0;

        for (int num : nums) {
            val |= num;
        }

        return val;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 54.72 MB (Beats: 61.97%)

<br>
