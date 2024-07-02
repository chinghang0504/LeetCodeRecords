# [LeetCode Records](../../README.md) - Question 2185 Counting Words With a Given Prefix

### Attempt 1: Check every character
```java
class Solution {
    public int prefixCount(String[] words, String pref) {
        int count = 0;

        for (String word : words) {
            int len = pref.length();
            if (word.length() < len) {
                continue;
            }

            boolean containPrefix = true;
            for (int i = 0; i < len; i++) {
                if (word.charAt(i) != pref.charAt(i)) {
                    containPrefix = false;
                    break;
                }
            }
            
            if (containPrefix) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 14.07%)
- Memory: 43.10 MB (Beats: 11.50%)

<br>

### Attempt 2: Use startsWith()
```java
class Solution {
    public int prefixCount(String[] words, String pref) {
        int count = 0;

        for (String word : words) {
            if (word.startsWith(pref)) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.44 MB (Beats: 92.12%)

<br>
