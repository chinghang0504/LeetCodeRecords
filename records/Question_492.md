# [LeetCode Records](../README.md) - Question 492 Construct the Rectangle

### Attempt 1: Start from the square root of area
```java
class Solution {
    public int[] constructRectangle(int area) {
        int w = (int)Math.sqrt(area);
        int l = area / w;
        
        while (l * w != area) {
            w--;
            l = area / w;
        }

        return new int[]{ l, w };
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.47 MB (Beats: 94.75%)

<br>
