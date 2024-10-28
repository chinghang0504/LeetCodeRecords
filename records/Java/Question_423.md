# [LeetCode Records](../../README.md) - Question 423 Reconstruct Original Digits from English

### Attempt 1: Use an int[] to store the character counts and an int[] to store the digit counts
```java
class Solution {
    public String originalDigits(String s) {
        int[] characterCounts = new int[26];
        for (char ch : s.toCharArray()) {
            characterCounts[ch - 'a']++;
        }

        int[] digitCounts = new int[10];
        digitCounts[0] = characterCounts['z' - 'a'];
        digitCounts[2] = characterCounts['w' - 'a'];
        digitCounts[4] = characterCounts['u' - 'a'];
        digitCounts[6] = characterCounts['x' - 'a'];
        digitCounts[8] = characterCounts['g' - 'a'];

        digitCounts[3] = characterCounts['h' - 'a'] - digitCounts[8];
        digitCounts[5] = characterCounts['f' - 'a'] - digitCounts[4];
        digitCounts[7] = characterCounts['s' - 'a'] - digitCounts[6];

        digitCounts[1] = characterCounts['o' - 'a'] - digitCounts[0] - digitCounts[2] - digitCounts[4];
        digitCounts[9] = characterCounts['i' - 'a'] - digitCounts[5] - digitCounts[6] - digitCounts[8];

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < 10; i++) {
            for (int j = 0; j < digitCounts[i]; j++) {
                stringBuilder.append((char)(i + '0'));
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.56 MB (Beats: 69.88%)

<br>
