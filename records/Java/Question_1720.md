# [LeetCode Records](../../README.md) - Question 1720 Decode XORed Array

### Attempt 1: Use ^ operator
```java
class Solution {
    public int[] decode(int[] encoded, int first) {
        int[] arr = new int[encoded.length + 1];
        arr[0] = first;

        for (int i = 0; i < encoded.length; i++) {
            arr[i + 1] = encoded[i] ^ arr[i];
        }

        return arr;
    }
}
```
- Runtime: 2 ms (Beats: 86.57%)
- Memory: 45.29 MB (Beats: 91.42%)

<br>
