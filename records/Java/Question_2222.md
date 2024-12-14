# [LeetCode Records](../../README.md) - Question 2222 Number of Ways to Select Buildings

### Attempt 1: Calculate the number of '01' and '10' patterns
```java
class Solution {
    public long numberOfWays(String s) {
        char[] arr = s.toCharArray();
        
        int[] zeroCounts = new int[arr.length];
        int[] oneCounts = new int[arr.length];
        for (int i = arr.length - 1, zeroCount = 0, oneCount = 0; i >= 0; i--) {
            if (arr[i] == '0') {
                zeroCount++;
            } else {
                oneCount++;
            }

            zeroCounts[i] = zeroCount;
            oneCounts[i] = oneCount;
        }

        long count = 0;
        int currZeroCount = 0;
        int currOneCount = 0;
        for (int i = 0; i < arr.length - 2;) {
            while (i < arr.length - 2 && arr[i] == '0') {
                currZeroCount++;
                i++;
            }

            currOneCount = 0;
            while (i < arr.length - 1 && arr[i] == '1') {
                currOneCount++;
                i++;
            }

            count += (long)currZeroCount * currOneCount * zeroCounts[i];
        }

        currZeroCount = 0;
        currOneCount = 0;
        for (int i = 0; i < arr.length - 2;) {
            while (i < arr.length - 2 && arr[i] == '1') {
                currOneCount++;
                i++;
            }

            currZeroCount = 0;
            while (i < arr.length - 1 && arr[i] == '0') {
                currZeroCount++;
                i++;
            }

            count += (long)currOneCount * currZeroCount * oneCounts[i];
        }

        return count;
    }
}
```
- Runtime: 34 ms (Beats: 46.13%)
- Memory: 45.94 MB (Beats: 41.94%)

<br>
