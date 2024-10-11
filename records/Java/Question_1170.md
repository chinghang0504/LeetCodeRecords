# [LeetCode Records](../../README.md) - Question 1170 Compare Strings by Frequency of the Smallest Character

### Attempt 1: Use an int[] to store the frequencies of the lexicographically smallest character of the words
```java
class Solution {
    public int[] numSmallerByFrequency(String[] queries, String[] words) {
        int[] wordFrequencies = new int[words.length];
        for (int i = 0; i < words.length; i++) {
            wordFrequencies[i] = getFrequency(words[i]);
        }

        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int count = 0;
            int frequency = getFrequency(queries[i]);

            for (int wordFrequency : wordFrequencies) {
                if (frequency < wordFrequency) {
                    count++;
                }
            }
            
            ans[i] = count;
        }

        return ans;
    }

    private int getFrequency(String word) {
        char currCh = 'z';
        int count = 0;
        for (char ch : word.toCharArray()) {
            if (ch < currCh) {
                currCh = ch;
                count = 1;
            } else if (ch == currCh) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 15 ms (Beats: 32.67%)
- Memory: 44.26 MB (Beats: 96.33%)

<br>
