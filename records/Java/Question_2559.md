# [LeetCode Records](../../README.md) - Question 2559 Count Vowel Strings in Ranges

### Attempt 1: Use an int[] to store the cumulative sums
```java
class Solution {
    public int[] vowelStrings(String[] words, int[][] queries) {
        int[] cumulativeSums = new int[words.length];
        if (isVowelString(words[0])) {
            cumulativeSums[0] = 1;
        }

        for (int i = 1; i < words.length; i++) {
            cumulativeSums[i] = isVowelString(words[i]) ? cumulativeSums[i - 1] + 1 : cumulativeSums[i - 1];
        }

        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            if (queries[i][0] == 0) {
                ans[i] = cumulativeSums[queries[i][1]];
            } else {
                ans[i] = cumulativeSums[queries[i][1]] - cumulativeSums[queries[i][0] - 1];
            }
        }

        return ans;
    }

    private boolean isVowelString(String str) {
        char ch1 = str.charAt(0);
        char ch2 = str.charAt(str.length() - 1);
        return isVowel(ch1) && isVowel(ch2);
    }

    private boolean isVowel(char ch) {
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
    }
}
```
- Runtime: 4 ms (Beats: 97.43%)
- Memory: 85.55 MB (Beats: 81.82%)

<br>
