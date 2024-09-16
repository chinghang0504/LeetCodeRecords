# [LeetCode Records](../../README.md) - Question 2221 Find Triangular Sum of an Array

### Attempt 1: Create a new int[] for each next array
```java
class Solution {
    public int triangularSum(int[] nums) {
        int[] prevArr = nums;
        
        while (prevArr.length > 1) {
            int[] nextArr = new int[prevArr.length - 1];

            for (int i = 0; i < nextArr.length; i++) {
                nextArr[i] = (prevArr[i] + prevArr[i + 1]) % 10;
            }
            
            prevArr = nextArr;
        }

        return prevArr[0];
    }
}
```
- Runtime: 46 ms (Beats: 45.66%)
- Memory: 44.93 MB (Beats: 19.62%)

<br>
