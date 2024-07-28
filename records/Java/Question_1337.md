# [LeetCode Records](../../README.md) - Question 1337 The K Weakest Rows in a Matrix

### Attempt 1: Use an int[][] to count the number of 1s and Arrays.sort()
```java
class Solution {
    public int[] kWeakestRows(int[][] mat, int k) {
        int m = mat.length;
        int n = mat[0].length;
        int[][] counts = new int[m][2];
        
        for (int i = 0; i < m; i++) {
            counts[i][1] = i;
            for (int j = 0; j < n; j++) {
                if (mat[i][j] == 1) {
                    counts[i][0]++;
                } else {
                    break;
                }
            }
        }

        Arrays.sort(counts, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[0] != o2[0] ? o1[0] - o2[0] : o1[1] - o2[1];
            }
        });

        int[] answer = new int[k];
        for (int i = 0; i < k; i++) {
            answer[i] = counts[i][1];
        }

        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 80.60%)
- Memory: 44.85 MB (Beats: 29.06%)

<br>
