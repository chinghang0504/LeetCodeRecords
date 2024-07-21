# [LeetCode Records](../../README.md) - Question 2273 Find Resultant Array After Removing Anagrams

### Attempt 1: Use a helper function to check is anagram
```java
class Solution {
    public List<String> removeAnagrams(String[] words) {
        for (int i = words.length - 1; i >= 1; i--) {
            if (isAnagram(words[i], words[i - 1])) {
                words[i] = null;
            }
        }

        List<String> answer = new ArrayList<>();
        for (String word : words) {
            if (word != null) {
                answer.add(word);
            }
        }

        return answer;
    }

    private boolean isAnagram(String str1, String str2) {
        int[] counts1 = new int[26];
        int[] counts2 = new int[26];

        for (char ch : str1.toCharArray()) {
            counts1[ch - 'a']++;
        }
        for (char ch : str2.toCharArray()) {
            counts2[ch - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            if (counts1[i] != counts2[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 93.02%)
- Memory: 44.82 MB (Beats: 15.90%)

<br>
