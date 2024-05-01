# [LeetCode Records](../../README.md) - Question 455 Assign Cookies

### Attempt 1: Sort two arrays first
```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);

        int count = 0;
        int gIndex = g.length - 1;
        int sIndex = s.length - 1;

        while (gIndex >= 0 && sIndex >= 0) {
            if (s[sIndex] >= g[gIndex]) {
                sIndex--;
                gIndex--;
                count++;
            } else {
                gIndex--;
            }
        }

        return count;
    }
}
```
- Runtime: 8 ms (Beats: 98.29%)
- Memory: 45.69 MB (Beats: 6.10%)

<br>
