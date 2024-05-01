# [LeetCode Records](../../README.md) - Question 28 Find the Index of the First Occurrence in a String

### Attempt 1: Find the first matched character and checl the remaininig
```java
class Solution {
    public int strStr(String haystack, String needle) {
        if (needle.length() > haystack.length()) {
            return -1;
        }

        for (int i = 0; i < haystack.length(); i++) {
            if (needle.length() > haystack.length() - i) {
                return -1;
            }

            if (haystack.charAt(i) == needle.charAt(0)) {
                int j = 1;
                boolean found = true;
                while (i + j < haystack.length() && j < needle.length()) {
                    if (haystack.charAt(i + j) != needle.charAt(j)) {
                        found = false;
                        break;
                    } else {
                        j++;
                    }
                }
                if (found) {
                    return i;
                }
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 31.67%)
- Memory: 41.23 MB (Beats: 72.91%)

<br>

### Attempt 2: Use substring() and equals()
```java
class Solution {
    public int strStr(String haystack, String needle) {
        int sourceLength = haystack.length();
        int targetLength = needle.length();

        if (targetLength > sourceLength) {
            return -1;
        }

        for (int i = 0; i < sourceLength; i++) {
            if (targetLength > sourceLength - i) {
                return -1;
            }

            String subString = haystack.substring(i, targetLength + i);
            if (subString.equals(needle)) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.47 MB (Beats: 43.68%)

<br>
