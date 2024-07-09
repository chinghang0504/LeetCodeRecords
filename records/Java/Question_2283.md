# [LeetCode Records](../../README.md) - Question 2283 Check if Number Has Equal Digit Count and Digit Value

### Attempt 1: Use an int[] to store the digits
```java
class Solution {
    public boolean digitCount(String num) {
        char[] arr = num.toCharArray();
        int[] counts = new int[10];

        for (char ch : arr) {
            counts[ch - '0']++;
        }

        for (int i = 0; i < arr.length; i++) {
            if (counts[i] != (arr[i] - '0')) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.51 MB (Beats: 69.29%)

<br>
