# [LeetCode Records](../../README.md) - Question 2570 Merge Two 2D Arrays by Summing Values

### Attempt 1: Use two indices to indicate the current elements of the arrays
```java
class Solution {
    public int[][] mergeArrays(int[][] nums1, int[][] nums2) {
        int[][] answer = new int[1001][2];
        int size = 0;

        int i = 0;
        int j = 0;
        while (i < nums1.length && j < nums2.length) {
            int id1 = nums1[i][0];
            int id2 = nums2[j][0];

            if (id1 == id2) {
                answer[size][0] = id1;
                answer[size][1] = nums1[i][1] + nums2[j][1];
                size++;
                i++;
                j++;
            } else if (id1 < id2) {
                answer[size][0] = id1;
                answer[size][1] = nums1[i][1];
                size++;
                i++;
            } else {
                answer[size][0] = id2;
                answer[size][1] = nums2[j][1];
                size++;
                j++;
            }
        }

        while (i < nums1.length) {
            answer[size][0] = nums1[i][0];
            answer[size][1] = nums1[i][1];
            size++;
            i++;
        }

        while (j < nums2.length) {
            answer[size][0] = nums2[j][0];
            answer[size][1] = nums2[j][1];
            size++;
            j++;
        }

        return Arrays.copyOf(answer, size);
    }
}
```
- Runtime: 2 ms (Beats: 63.15%)
- Memory: 45.53 MB (Beats: 11.69%)

<br>
