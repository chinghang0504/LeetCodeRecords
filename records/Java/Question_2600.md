# [LeetCode Records](../../README.md) - Question 2600 K Items With the Maximum Sum

### Attempt 1: Use two if-else statements
```java
class Solution {
    public int kItemsWithMaximumSum(int numOnes, int numZeros, int numNegOnes, int k) {
        int sum = 0;
        
        if (k >= numOnes) {
            sum += numOnes;
            k -= numOnes; 
        } else {
            return k;
        }

        if (k >= numZeros) {
            k -= numZeros;
        } else {
            return sum;
        }

        return sum - k;
    }
}
```
- Runtime: 1 ms (Beats: 83.65%)
- Memory: 40.90 MB (Beats: 73.08%)

<br>
