# [LeetCode Records](../../README.md) - Question 541 Reverse String II

### Attempt 1: Use a helper function to reverse the characters in the array
```java
class Solution {
    public String reverseStr(String s, int k) {
        char[] arr = s.toCharArray();
        int twoK = 2 * k;

        int i = 0;
        for (; i + twoK <= arr.length; i += twoK) {
            reverseArr(arr, i, i + k);
        }
        reverseArr(arr, i, Math.min(arr.length, i + k));

        return new String(arr);
    }

    private void reverseArr(char[] arr, int start, int end) {
        int step = (end - start) / 2;
        for (int i = 0; i < step; i++) {
            char temp = arr[start + i];
            arr[start + i] = arr[end - i - 1];
            arr[end - i - 1] = temp;
        }
    }
}
```
- Runtime: 1 ms (Beats: 83.24%)
- Memory: 43.83 MB (Beats: 18.87%)

<br>
