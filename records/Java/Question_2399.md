# [LeetCode Records](../../README.md) - Question 2399 Check Distances Between Same Letters

### Attempt 1: Use a boolean[] to record if the character is checked
```java
class Solution {
    public boolean checkDistances(String s, int[] distance) {
        char[] arr = s.toCharArray();
        boolean[] checked = new boolean[26];

        for (int i = 0; i < arr.length; i++) {
            char ch = arr[i];
            int chIndex = ch - 'a';

            if (!checked[chIndex]) {
                int targetIndex = i + distance[chIndex] + 1;
                if (targetIndex >= arr.length || arr[targetIndex] != ch) {
                    return false;
                }
                checked[chIndex] = true;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 92.95%)
- Memory: 42.58 MB (Beats: 61.00%)

<br>
