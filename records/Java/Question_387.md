# [LeetCode Records](../../README.md) - Question 387 First Unique Character in a String

### Attempt 1: Use an int array to record
```java
class Solution {
    public int firstUniqChar(String s) {
        int[] saved = new int[26];

        char[] arr = s.toCharArray();
        for (int i = 0; i < arr.length; i++) {
            saved[arr[i] - 'a']++;
        }

        for (int i = 0; i < arr.length; i++) {
            if (saved[arr[i] - 'a'] == 1) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 4 ms (Beats: 95.41%)
- Memory: 45.28 MB (Beats: 24.21%)

<br>

### Attempt 2: Use indexOf() and lastIndexOf()
```java
class Solution {
    public int firstUniqChar(String s) {
        int min = Integer.MAX_VALUE;

        for (char ch = 'a'; ch <= 'z'; ch++) {
            int startIndex = s.indexOf(ch);
            if (startIndex != -1 && startIndex == s.lastIndexOf(ch)) {
                min = Math.min(min, startIndex);
            }
        }

        return min == Integer.MAX_VALUE ? -1 : min;
    }
}
```
- Runtime: 4 ms (Beats: 95.41%)
- Memory: 45.10 MB (Beats: 36.64%)

<br>
