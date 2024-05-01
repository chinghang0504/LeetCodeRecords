# [LeetCode Records](../../README.md) - Question 14 Longest Common Prefix

### Attempt 1: Find the minimum number of characters and compare to each characters
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        int min = strs[0].length();
        for (int i = 1; i < strs.length; i++) {
            if (strs[i].length() < min) {
                min = strs[i].length();
            }
        }

        int i = 0;
        for (; i < min; i++) {
            char ch = strs[0].charAt(i);
            for (int j = 1; j < strs.length; j++) {
                if (strs[j].charAt(i) != ch) {
                    return strs[0].substring(0, i);
                }
            }
        }

        return strs[0].substring(0, i);
    }
}
```
- Runtime: 1 ms (Beats: 77.33%)
- Memory: 41.41 MB (Beats: 53.74%)

<br>

### Attempt 2: Use Arrays.sort()
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        Arrays.sort(strs);
        String s1 = strs[0];
        String s2 = strs[strs.length - 1];
        int min = Math.min(s1.length(), s2.length());

        for (int i = 0; i < min; i++) {
            if (s1.charAt(i) != s2.charAt(i)) {
                return s1.substring(0, i);
            }
        }

        return s1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.20 MB (Beats: 75.79%)

<br>
