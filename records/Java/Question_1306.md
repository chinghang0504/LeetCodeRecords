# [LeetCode Records](../../README.md) - Question 1306 

### Attempt 1: Use a boolean[] to store the indices that are checked
```java
class Solution {
    public boolean canReach(int[] arr, int start) {
        boolean[] checked = new boolean[arr.length];

        return canReachRecursion(arr, checked, start);
    }

    private boolean canReachRecursion(int[] arr, boolean[] checked, int curr) {
        if (curr < 0 || curr >= arr.length || checked[curr]) {
            return false;
        }

        checked[curr] = true;

        if (arr[curr] == 0) {
            return true;
        }

        if (canReachRecursion(arr, checked, curr - arr[curr])) {
            return true;
        }
        if (canReachRecursion(arr, checked, curr + arr[curr])) {
            return true;
        }

        return false;
    }
}
```
- Runtime: 2 ms (Beats: 84.22%)
- Memory: 58.69 MB (Beats: 40.35%)

<br>
