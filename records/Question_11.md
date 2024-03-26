# [LeetCode Records](../README.md) - Question 11 Container With Most Water

### Attempt 1: Calculate the area at each time
```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0, j = height.length - 1;
        int max = 0;

        while (i != j) {
            int area = Math.min(height[i], height[j]) * (j - i);
            if (area > max) {
                max = area;
            }

            if (height[i] > height[j]) {
                j--;
            } else {
                i++;
            }
        }

        return max;
    }
}
```
- Runtime: 4 ms (Beats: 88.77%)
- Memory: 57.92 MB (Beats: 38.91%)

<br>

### Attempt 2: Stop calculate the area when height <= minHeigth
```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0, j = height.length - 1;
        int maxWater = 0;

        while (i < j) {
            int minHeight = Math.min(height[i], height[j]);
            int water = minHeight * (j - i);
            if (water > maxWater) {
                maxWater = water;
            }

            while (i < j && height[i] <= minHeight) {
                i++;
            }
            while (i < j && height[j] <= minHeight) {
                j--;
            }
        }

        return maxWater;
    }
}
```
- Runtime: 2 ms (Beats: 99.32%)
- Memory: 58.07 MB (Beats: 30.74%)

<br>
