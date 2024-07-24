# [LeetCode Records](../../README.md) - Question 2103 Rings and Rods

### Attempt 1: Use three boolean[] to record the number of colors on rods
```java
class Solution {
    public int countPoints(String rings) {
        boolean[] red = new boolean[10];
        boolean[] green = new boolean[10];
        boolean[] blue = new boolean[10];
        char[] arr = rings.toCharArray();

        for (int i = 0; i < arr.length; i += 2) {
            int rod = arr[i + 1] - '0';
            if (arr[i] == 'R') {
                red[rod] = true;
            } else if (arr[i] == 'G') {
                green[rod] = true;
            } else {
                blue[rod] = true;
            }
        }

        int count = 0;
        for (int i = 0; i < 10; i++) {
            if (red[i] && green[i] && blue[i]) {
                count++;
            }
        }
        
        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.80 MB (Beats: 98.81%)

<br>
