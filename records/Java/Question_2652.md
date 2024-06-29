# [LeetCode Records](../../README.md) - Question 2652 Sum Multiples

### Attempt 1: Test each number
```java
class Solution {
    public int sumOfMultiples(int n) {
        int sum = 0;

        for (int i = 0; i <= n; i++) {
            if (i % 3 == 0 || i % 5 == 0 || i % 7 == 0) {
                sum += i;
            }
        }

        return sum;
    }
}
```
- Runtime: 2 ms (Beats: 96.45%)
- Memory: 40.51 MB (Beats: 68.36%)

<br>
