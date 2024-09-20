# [LeetCode Records](../../README.md) - Question 1529 Minimum Suffix Flips

### Attempt 1: Start from the leftmost '1'
```java
class Solution {
    public int minFlips(String target) {
        char[] arr = target.toCharArray();
        
        int i = 0;
        while (i < arr.length && arr[i] == '0') {
            i++;
        }

        if (i >= arr.length) {
            return 0;
        }

        int numOfGroups = 1;
        i++;
        while (i < arr.length) {
            if (arr[i - 1] != arr[i]) {
                numOfGroups++;
            }
            i++;
        }

        return numOfGroups;
    }
}
```
- Runtime: 5 ms (Beats: 76.33%)
- Memory: 44.58 MB (Beats: 60.95%)

<br>
