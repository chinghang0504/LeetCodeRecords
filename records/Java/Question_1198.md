# [LeetCode Records](../../README.md) - Question 1198 Find Smallest Common Element in All Rows

### Attempt 1: Check every element from the first array
```java
class Solution {
    public int smallestCommonElement(int[][] mat) {
        int[] firstArr = mat[0];

        for (int num : firstArr) {
            boolean foundTarget = true;
            
            for (int i = 1; i < mat.length; i++) {
                if (!hasTarget(mat[i], num)) {
                    foundTarget = false;
                    break;
                }
            }

            if (foundTarget) {
                return num;
            }
        }

        return -1;
    }

    private boolean hasTarget(int[] arr, int target) {
        for (int i = 0; i < arr.length && target >= arr[i]; i++) {
            if (arr[i] == target) {
                return true;
            }
        }
        
        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 67.49 MB (Beats: 64.52%)

<br>
