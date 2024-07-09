# [LeetCode Records](../../README.md) - Question 1460 Make Two Arrays Equal by Reversing Subarrays

### Attempt 1: Use Arrays.sort() twice
```java
class Solution {
    public boolean canBeEqual(int[] target, int[] arr) {
        Arrays.sort(target);
        Arrays.sort(arr);

        for (int i = 0; i < target.length; i++) {
            if (target[i] != arr[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 85.33%)
- Memory: 44.18 MB (Beats: 51.29%)

<br>
