# [LeetCode Records](../../README.md) - Question 848 Shifting Letters

### Attempt 1: Track the current sum of shifts
```java
class Solution {
    public String shiftingLetters(String s, int[] shifts) {
        char[] arr = s.toCharArray();

        for (int i = arr.length - 1, currSum = 0; i >= 0; i--) {
            currSum += shifts[i] % 26;
            arr[i] = (char)((arr[i] - 'a' + currSum) % 26 + 'a');
        }

        return new String(arr);
    }
}
```
- Runtime: 5 ms (Beats: 98.99%)
- Memory: 55.47 MB (Beats: 84.92%)

<br>
