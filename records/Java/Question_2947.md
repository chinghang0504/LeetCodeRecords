# [LeetCode Records](../../README.md) - Question 2947 Count Beautiful Substrings I

### Attempt 1: Use an int[][] to store the cumulative vowel and consonant counts
```java
class Solution {
    public int beautifulSubstrings(String s, int k) {
        char[] arr = s.toCharArray();
        int[][] counts = new int[arr.length + 1][2];
        for (int i = 1; i <= arr.length; i++) {
            if (isVowel(arr[i - 1])) {
                counts[i][0] = counts[i - 1][0] + 1;
                counts[i][1] = counts[i - 1][1];
            } else {
                counts[i][0] = counts[i - 1][0];
                counts[i][1] = counts[i - 1][1] + 1;
            }
        }

        int count = 0;
        for (int i = 2; i <= arr.length; i += 2) {
            for (int j = 0; j < arr.length - i + 1; j++) {
                int vowelCount = counts[j + i][0] - counts[j][0];
                int consonantCount = counts[j + i][1] - counts[j][1];
                if (vowelCount == consonantCount && vowelCount * consonantCount % k == 0) {
                    count++;
                }
            }
        }

        return count;
    }

    private boolean isVowel(char ch) {
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
    }
}
```
- Runtime: 20 ms (Beats: 89.40%)
- Memory: 43.90 MB (Beats: 21.57%)

<br>
