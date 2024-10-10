# [LeetCode Records](../../README.md) - Question 835 Image Overlap

### Attempt 1: Use an ArrayList to store the positions of 1 in image 1
```java
class Solution {
    public int largestOverlap(int[][] img1, int[][] img2) {
        int n = img1.length;
        List<int[]> list = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (img1[i][j] == 1) {
                    list.add(new int[]{ i, j });
                }
            }
        }

        int size = list.size();
        int maxCount = 0;
        for (int i = - (n - 1); i < n; i++) {
            for (int j = - (n - 1); j < n; j++) {
                maxCount = Math.max(maxCount, getCount(img2, n, list, i, j));
                if (maxCount == size) {
                    return maxCount;
                }
            }
        }

        return maxCount;
    }

    private int getCount(int[][] img2, int n, List<int[]> list, int startI, int startJ) {
        int count = 0;

        for (int[] position : list) {
            int i = startI + position[0];
            int j = startJ + position[1];

            if (i >= 0 && i < n && j >= 0 && j < n && img2[i][j] == 1) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 71 ms (Beats: 27.70%)
- Memory: 44.16 MB (Beats: 29.11%)

<br>
