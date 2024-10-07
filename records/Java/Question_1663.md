# [LeetCode Records](../../README.md) - Question 1663 Smallest String With A Given Numeric Value

### Attempt 1: Use an int[] store the character values
```java
class Solution {
    public String getSmallestString(int n, int k) {
        int[] characters = new int[n];
        for (int i = 0; i < n; i++) {
            characters[i] = 1;
        }
        k -= n;

        int lastIndex = n - 1;
        while (k > 0) {
            if (k >= 25) {
                characters[lastIndex] += 25;
                k -= 25;
            } else {
                characters[lastIndex] += k;
                k = 0;
            }
            
            lastIndex--;
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < n; i++) {
            stringBuilder.append((char)(characters[i] + 'a' - 1));
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 29 ms (Beats: 20.22%)
- Memory: 45.49 MB (Beats: 7.86%)

<br>
