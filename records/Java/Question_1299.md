# [LeetCode Records](../../README.md) - Question 1299 Replace Elements with Greatest Element on Right Side

### Attempt 1: 
```java
class Solution {
    public int[] replaceElements(int[] arr) {
        int[] result = new int[arr.length];

        for (int i = 0; i < arr.length - 1; i++) {
            int max = arr[i + 1];
            for (int j = i + 2; j < arr.length; j++) {
                max = Math.max(max, arr[j]);
            }
            result[i] = max;
        }
        result[arr.length - 1] = -1;

        return result;
    }
}
```
- Runtime: 1103 ms (Beats: 6.10%)
- Memory: 46.54 MB (Beats: 30.06%)

<br>

### Attempt 2: Start from right
```java
class Solution {
    public int[] replaceElements(int[] arr) {
        int[] result = new int[arr.length];

        int maxRight = -1;

        for (int i = arr.length - 1; i >= 0; i--) {
            result[i] = maxRight;
            if (maxRight < arr[i]) {
                maxRight = arr[i];
            }
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 46.58 MB (Beats: 30.06%)

<br>
