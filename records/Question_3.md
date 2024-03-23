# [LeetCode Records](../README.md) - Question 3 Longest Substring Without Repeating Characters

### Attempt 1: Use HashMap
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int longestLength = 0;
        HashMap<Character, Integer> hashMap = new HashMap<Character, Integer>();
        int currLength = 0;
        int currStratIndex = 0;
        int length = s.length();

        for (int i = 0; i < length; i++) {
            char ch = s.charAt(i);
            Integer index = hashMap.get(ch);
            if (index == null) {
                hashMap.put(ch, i);
                currLength++;
                continue;
            }

            if (currLength > longestLength) {
                longestLength = currLength;
            }
            for (int j = index; currStratIndex <= j; j--) {
                hashMap.remove(s.charAt(j));
                currLength--;
            }
            currStratIndex = index + 1;
            hashMap.put(ch, i);
            currLength++;
        }
        if (currLength > longestLength) {
            longestLength = currLength;
        }

        return longestLength;
    }
}
```
- Runtime: 6 ms (Beats: 69.74%)
- Memory: 44.63 MB (Beats: 44.31%)

<br>

### Attempt 2: Eliminate the calling of remove()
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> hashMap = new HashMap<Character, Integer>();
        int start = 0;
        int maxLength = 0;

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            Integer index = hashMap.get(ch);
            if (index != null && index >= start) {
                start = index + 1;
            }

            maxLength = Math.max(maxLength, i - start + 1);
            hashMap.put(ch, i);
        }

        return maxLength;
    }
}
```
- Runtime: 4 ms (Beats: 89.49%)
- Memory: 44.39 MB (Beats: 72.39%)

<br>
