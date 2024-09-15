# [LeetCode Records](../../README.md) - Question 966 Vowel Spellchecker

### Attempt 1: Use a HashSet to store the original words, a HashMap to store the lower case words, and a HashMap to store the fixed vowel words
```java
class Solution {
    public String[] spellchecker(String[] wordlist, String[] queries) {
        Set<String> originalSet = new HashSet<>();
        Map<String, String> lowerCaseMap = new HashMap<>();
        Map<String, String> fixedVowelMap = new HashMap<>();

        for (String word : wordlist) {
            originalSet.add(word);

            String lowerCaseWord = word.toLowerCase();
            if (!lowerCaseMap.containsKey(lowerCaseWord)) {
                lowerCaseMap.put(lowerCaseWord, word);
            }

            String fixedVowelWord = fixVowel(lowerCaseWord);
            if (!fixedVowelMap.containsKey(fixedVowelWord)) {
                fixedVowelMap.put(fixedVowelWord, word);
            }
        }

        String[] ans = new String[queries.length];
        int i = 0;
        for (String query : queries) {
            String result = "";
            if (originalSet.contains(query)) {
                result = query;
            } else {
                String lowerCaseQuery = query.toLowerCase();
                String val = lowerCaseMap.get(lowerCaseQuery);
                if (val != null) {
                    result = val;
                } else {
                    val = fixedVowelMap.get(fixVowel(lowerCaseQuery));
                    if (val != null) {
                        result = val;
                    }
                }
            }

            ans[i] = result;
            i++;
        }

        return ans;
    }

    private String fixVowel(String str) {
        char[] arr = str.toCharArray();
        for (int i = 0; i < arr.length; i++) {
            if (isVowel(arr[i])) {
                arr[i] = 'a';
            }
        }
        return new String(arr);
    }

    private boolean isVowel(char ch) {
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
    }
}
```
- Runtime: 21 ms (Beats: 78.72%)
- Memory: 47.62 MB (Beats: 76.60%)

<br>
