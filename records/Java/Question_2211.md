# [LeetCode Records](../../README.md) - Question 2211 Count Collisions on a Road

### Attempt 1: Find the first index that is not a 'L' and the last index that is not a 'R'
```java
class Solution {
    public int countCollisions(String directions) {
        char[] arr = directions.toCharArray();
        
        int start = 0;
        while (start < arr.length) {
            if (arr[start] == 'L') {
                start++;
            } else {
                break;
            }
        }

        int end = arr.length - 1;
        while (end >= 0) {
            if (arr[end] == 'R') {
                end--;
            } else {
                break;
            }
        }

        int count = 0;
        for (int i = start; i <= end; i++) {
            if (arr[i] != 'S') {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 8 ms (Beats: 100.00%)
- Memory: 45.48 MB (Beats: 50.54%)

<br>
