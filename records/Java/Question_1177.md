# [LeetCode Records](../../README.md) - Question 1177 Can Make Palindrome from Substring

### Attempt 1: Use an int[][] to store the character counts
```java
class Solution {
    public List<Boolean> canMakePaliQueries(String s, int[][] queries) {
        char[] arr = s.toCharArray();
        int[][] characterCounts = new int[arr.length][26];
        characterCounts[0][arr[0] - 'a']++;
        for (int i = 1; i < arr.length; i++) {
            for (int j = 0; j < 26; j++) {
                characterCounts[i][j] = characterCounts[i - 1][j];
            }
            characterCounts[i][arr[i] - 'a']++;
        }

        List<Boolean> ans = new ArrayList<>();
        for (int[] query : queries) {
            int singleCount = 0;
            if (query[0] == 0) {
                for (int i = 0; i < 26; i++) {
                    int count = characterCounts[query[1]][i];
                    if (count % 2 == 1) {
                        singleCount++;
                    }
                }
            } else {
                for (int i = 0; i < 26; i++) {
                    int count = characterCounts[query[1]][i] - characterCounts[query[0] - 1][i];
                    if (count % 2 == 1) {
                        singleCount++;
                    }
                }
            }

            ans.add(singleCount / 2 <= query[2]);
        }
        
        return ans;
    }
}
```
- Runtime: 46 ms (Beats: 48.78%)
- Memory: 105.36 MB (Beats: 70.48%)

<br>
