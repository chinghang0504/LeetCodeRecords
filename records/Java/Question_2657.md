# [LeetCode Records](../../README.md) - Question 2657 Find the Prefix Common Array of Two Arrays

### Attempt 1: Use an int[] to save the number counts
```java
class Solution {
    public int[] findThePrefixCommonArray(int[] A, int[] B) {
        int size = A.length;
        int[] ans = new int[size];
        int[] counts = new int[size + 1];

        int currCount = 0;
        for (int i = 0; i < size; i++) {
            counts[A[i]]++;
            counts[B[i]]++;

            if (counts[A[i]] == 2) {
                currCount++;
            }
            if (A[i] != B[i] && counts[B[i]] == 2) {
                currCount++;
            }

            ans[i] = currCount;
        }

        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 94.52%)
- Memory: 45.26 MB (Beats: 84.88%)

<br>
