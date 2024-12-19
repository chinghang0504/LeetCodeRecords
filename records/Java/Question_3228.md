# [LeetCode Records](../../README.md) - Question 3228 Maximum Number of Operations to Move Ones to the End

### Attempt 1: Track the rank of zero group
```java
class Solution {
    public int maxOperations(String s) {
        char[] arr = s.toCharArray();
        int count = 0;

        int currZeroFactor = 0;
        int i = arr.length - 1;
        while (i >= 0 && arr[i] == '1') {
            i--;
        }

        while (i >= 0) {
            currZeroFactor++;
            while (i >= 0 && arr[i] == '0') {
                i--;
            }

            int oneCount = 0;
            while (i >= 0 && arr[i] == '1') {
                i--;
                oneCount++;
            }

            count += oneCount * currZeroFactor;
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 100.00%)
- Memory: 45.33 MB (Beats: 57.72%)

<br>
