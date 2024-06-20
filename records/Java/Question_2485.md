# [LeetCode Records](../../README.md) - Question 2485 Find the Pivot Integer

### Attempt 1: Use binary search
```java
class Solution {
    public int pivotInteger(int n) {
        int start = 1;
        int end = n;
        int total = (1 + n) * n / 2;

        while (start <= end) {
            int middle = (start + end) / 2;
            int leftVal = (1 + middle) * middle / 2;
            int rightVal = total - leftVal + middle;
            
            if (leftVal == rightVal) {
                return middle;
            } else if (leftVal > rightVal) {
                end = middle - 1;
            } else {
                start = middle + 1;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.38 MB (Beats: 66.69%)

<br>
