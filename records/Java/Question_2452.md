# [LeetCode Records](../../README.md) - Question 2452 Words Within Two Edits of Dictionary

### Attempt 1: Use brute force algorithm
```java
class Solution {
    public List<String> twoEditWords(String[] queries, String[] dictionary) {
        char[][] words = new char[dictionary.length][];

        for (int i = 0; i < dictionary.length; i++) {
            words[i] = dictionary[i].toCharArray();
        }

        List<String> ans = new ArrayList<>();
        for (String query : queries) {
            char[] queryWord = query.toCharArray();

            for (char[] word : words) {
                if (isValid(queryWord, word)) {
                    ans.add(query);
                    break;
                }
            }
        }

        return ans;
    }

    private boolean isValid(char[] arr1, char[] arr2) {
        int count = 0;
        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] != arr2[i]) {
                count++;

                if (count > 2) {
                    return false;
                }
            }
        }
        return true;
    }
}
```
- Runtime: 2 ms (Beats: 93.02%)
- Memory: 42.98 MB (Beats: 37.92%)

<br>
