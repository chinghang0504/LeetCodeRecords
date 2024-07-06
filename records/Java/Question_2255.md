# [LeetCode Records](../../README.md) - Question 2255 Count Prefixes of a Given String

### Attempt 1: Compare the string length
```java
class Solution {
    public int countPrefixes(String[] words, String s) {
        int targetSize = s.length();
        int count = 0;

        for (String word : words) {
            int wordSize = word.length();
            if (wordSize > targetSize) {
                continue;
            } else if (wordSize == targetSize) {
                if (word.equals(s)) {
                    count++;
                }
            } else {
                if (word.equals(s.substring(0, wordSize))) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 54.80%)
- Memory: 44.12 MB (Beats: 11.30%)

<br>

### Attempt 2: Use indexOf()
```java
class Solution {
    public int countPrefixes(String[] words, String s) {
        int count = 0;

        for (String word : words) {
            if (s.indexOf(word) == 0) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 54.80%)
- Memory: 43.12 MB (Beats: 63.47%)

<br>

### Attempt 3: Use startWith()
```java
class Solution {
    public int countPrefixes(String[] words, String s) {
        int count = 0;

        for (String word : words) {
            if (s.startsWith(word)) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.13 MB (Beats: 63.47%)

<br>
