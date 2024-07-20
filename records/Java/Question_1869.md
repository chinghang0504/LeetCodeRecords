# [LeetCode Records](../../README.md) - Question 1869 Longer Contiguous Segments of Ones than Zeros

### Attempt 1: Use boolean variable to track the current contiguous segment of ones or zeros
```java
class Solution {
    public boolean checkZeroOnes(String s) {
        int maxOnesLength = 0;
        int maxZerosLength = 0;
        boolean isOne = true;
        int length = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '1') {
                if (isOne) {
                    length++;
                } else {
                    maxZerosLength = Math.max(maxZerosLength, length);
                    length = 1;
                    isOne = true;
                }
            } else {
                if (isOne) {
                    maxOnesLength = Math.max(maxOnesLength, length);
                    length = 1;
                    isOne = false;
                } else {
                    length++;
                }
            }
        }
        if (isOne) {
            maxOnesLength = Math.max(maxOnesLength, length);
        } else {
            maxZerosLength = Math.max(maxZerosLength, length);
        }

        return maxOnesLength > maxZerosLength;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.52 MB (Beats: 15.23%)

<br>
