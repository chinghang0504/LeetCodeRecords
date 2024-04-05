# [LeetCode Records](../README.md) - Question 242 Valid Anagram

### Attempt 1: Use two arrays
```java
class Solution {

    public boolean isAnagram(String s, String t) {
        int size = s.length();
        if (t.length() != size) {
            return false;
        }

        int[] count1 = new int[26];
        for (int i = 0; i < size; i++) {
            count1[s.charAt(i) - 'a']++;
        }

        int[] count2 = new int[26];
        for (int i = 0; i < size; i++) {
            count2[t.charAt(i) - 'a']++;
        }

        return Arrays.equals(count1, count2);
    }
}
```
- Runtime: 3 ms (Beats: 89.58%)
- Memory: 42.80 MB (Beats: 89.08%)

<br>

### Attempt 2: Use an array
```java
class Solution {

    public boolean isAnagram(String s, String t) {
        int size = s.length();
        if (t.length() != size) {
            return false;
        }

        int[] count = new int[26];
        for (char ch : s.toCharArray()) {
            count[ch - 'a']++;
        }
        for (char ch : t.toCharArray()) {
            count[ch - 'a']--;
        }

        for (int i : count) {
            if (i != 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 99.80%)
- Memory: 43.01 MB (Beats: 74.67%)

<br>
