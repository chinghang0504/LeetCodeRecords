# [LeetCode Records](../../README.md) - Question 1806 Minimum Number of Operations to Reinitialize a Permutation

### Attempt 1: Loop until becomes original array
```java
class Solution {
    public int reinitializePermutation(int n) {
        int[] perm = new int[n];
        for (int i = 0; i < n; i++) {
            perm[i] = i;
        }

        int count = 0;
        do {
            perm = executeOperation(perm);
            count++;
        } while (!isOriginal(perm));

        return count;
    }

    private int[] executeOperation(int[] perm) {
        int n = perm.length;
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = i % 2 == 0 ? perm[i / 2] : perm[n / 2 + (i - 1) / 2];
        }
        return arr;
    }

    private boolean isOriginal(int[] perm) {
        for (int i = 0; i < perm.length; i++) {
            if (perm[i] != i) {
                return false;
            }
        }
        return true;
    }
}
```
- Runtime: 19 ms (Beats: 59.52%)
- Memory: 44.48 MB (Beats: 11.90%)

<br>
