# [LeetCode Records](../../README.md) - Question 2442 Count Number of Distinct Integers After Reverse Operations

### Attempt 1: Use a HashSet to store the numbers and the reversed numbers
```java
class Solution {
    public int countDistinctIntegers(int[] nums) {
        Set<Integer> set = new HashSet<>();

        for (int num : nums) {
            set.add(num);
            set.add(reversedInteger(num));
        }

        return set.size();
    }

    private int reversedInteger(int num) {
        int val = 0;
        while (num > 0) {
            val *= 10;
            val += num % 10;
            num /= 10;
        }
        return val;
    }
}
```
- Runtime: 57 ms (Beats: 76.45%)
- Memory: 68.55 MB (Beats: 11.51%)

<br>
