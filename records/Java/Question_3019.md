# [LeetCode Records](../../README.md) - Question 3019 Number of Changing Keys

### Attempt 1: Use a loop and Character.toLowerCase()
```java
class Solution {
    public int countKeyChanges(String s) {
        int count = 0;
        char[] arr = s.toCharArray();

        for (int i = 1; i < arr.length; i++) {
            char prevCh = arr[i - 1];
            char currCh = arr[i];

            if (prevCh != currCh && Character.toLowerCase(prevCh) != Character.toLowerCase(currCh)) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 99.93%)
- Memory: 42.39 MB (Beats: 13.30%)

<br>
