# [LeetCode Records](../../README.md) - Question 38 Count and Say

### Attempt 1: Use recursion
```java
class Solution {
    public String countAndSay(int n) {
        // Base case
        if (n == 1) {
            return "1";
        }

        // Get the previous result
        StringBuilder stringBuilder = new StringBuilder();
        String prevResult = countAndSay(n - 1);
        int prevSize = prevResult.length();

        // Count the current character
        char currCh = prevResult.charAt(0);
        int currCount = 1;
        for (int i = 1; i < prevSize; i++) {
            char ch = prevResult.charAt(i);
            if (ch == currCh) {
                currCount++;
            } else {
                stringBuilder.append(currCount).append(currCh);
                currCh = ch;
                currCount = 1;
            }
        }
        stringBuilder.append(currCount).append(currCh);

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 99.28%)
- Memory: 41.43 MB (Beats: 45.60%)

<br>
