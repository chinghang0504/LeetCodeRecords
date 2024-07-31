# [LeetCode Records](../../README.md) - Question 953 Verifying an Alien Dictionary

### Attempt 1: Use a HashMap to save the character indices and a helper function to compare two strings
```java
class Solution {
    public boolean isAlienSorted(String[] words, String order) {
        Map<Character, Integer> map = new HashMap<>();
        char[] arr = order.toCharArray();

        for (int i = 0; i < 26; i++) {
            map.put(arr[i], i);
        }
        
        for (int i = 0; i < words.length - 1; i++) {
            if (compare(map, words[i], words[i + 1]) > 0) {
                return false;
            }
        }

        return true;
    }

    private int compare(Map<Character, Integer> map, String word1, String word2) {
        int size1 = word1.length();
        int size2 = word2.length();
        int minSize = Math.min(size1, size2);

        for (int i = 0; i < minSize; i++) {
            char ch1 = word1.charAt(i);
            char ch2 = word2.charAt(i);

            if (ch1 != ch2) {
                return map.get(ch1) - map.get(ch2);
            }
        }

        return size1 - size2;
    }
}
```
- Runtime: 1 ms (Beats: 56.85%)
- Memory: 41.95 MB (Beats: 53.56%)

<br>
