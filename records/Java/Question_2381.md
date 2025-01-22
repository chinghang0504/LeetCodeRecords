# [LeetCode Records](../../README.md) - Question 2381 Shifting Letters II

### Attempt 1: Use an int[] to store the prefix sums
```java
class Solution {
    public String shiftingLetters(String s, int[][] shifts) {
        char[] arr = s.toCharArray();
        int[] prefixSums = new int[arr.length];

        for (int[] shift : shifts) {
            int start = shift[0];
            int end = shift[1] + 1;
            int direction = shift[2];

            if (direction == 1) {
                prefixSums[start]++;
                if (end < arr.length) {
                    prefixSums[end]--;
                }
            } else {
                prefixSums[start]--;
                if (end < arr.length) {
                    prefixSums[end]++;
                }
            }
        }

        int prefixSum = 0;
        for (int i = 0; i < arr.length; i++) {
            prefixSum += prefixSums[i];
            arr[i] = (char)((arr[i] - 'a' + prefixSum % 26 + 26) % 26 + 'a');
        }

        return new String(arr);
    }
}
```
- Runtime: 6 ms (Beats: 95.65%)
- Memory: 74.00 MB (Beats: 91.29%)

<br>
