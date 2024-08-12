# [LeetCode Records](../../README.md) - Question 661 Image Smoother

### Attempt 1: Use a helper function to calculate the average for each entry
```java
class Solution {
    public int[][] imageSmoother(int[][] img) {
        int m = img.length;
        int n = img[0].length;
        int[][] answer = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                answer[i][j] = getAverage(img, m, n, i, j);
            }
        }

        return answer;
    }

    private int getAverage(int[][] img, int m, int n, int centerI, int centerJ) {
        int sum = 0;
        int count = 0;
        int startI = centerI - 1 >= 0 ? centerI - 1 : centerI;
        int endI = centerI + 1 < m ? centerI + 1 : centerI;
        int startJ = centerJ - 1 >= 0 ? centerJ - 1 : centerJ;
        int endJ = centerJ + 1 < n ? centerJ + 1 : centerJ;
        
        for (int i = startI; i <= endI; i++) {
            for (int j = startJ; j <= endJ; j++) {
                sum += img[i][j];
                count++;
            }
        }

        return sum / count;
    }
}
```
- Runtime: 4 ms (Beats: 93.40%)
- Memory: 45.72 MB (Beats: 30.29%)

<br>
