# [LeetCode Records](../../README.md) - Question 832 Flipping an Image

### Attempt 1: 
```java
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        int n = image.length;

        for (int[] row : image) {
            for (int i = 0; i < n / 2; i++) {
                int temp = row[i];
                row[i] = row[n - 1 - i] == 1 ? 0 : 1;
                row[n - 1 - i] = temp == 1 ? 0 : 1;
            }
            if (n % 2 == 1) {
                row[n / 2] = row[n / 2] == 1 ? 0 : 1;
            }
        }

        return image;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.52 MB (Beats: 35.64%)

<br>
