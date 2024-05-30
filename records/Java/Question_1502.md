# [LeetCode Records](../../README.md) - Question 1502 Can Make Arithmetic Progression From Sequence

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public boolean canMakeArithmeticProgression(int[] arr) {
        Arrays.sort(arr);

        int diff = arr[1] - arr[0];
        for (int i = 2; i < arr.length; i++) {
            if (arr[i] - arr[i - 1] != diff) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 97.26%)
- Memory: 42.44 MB (Beats: 7.20%)

<br>
