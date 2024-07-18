# [LeetCode Records](../../README.md) - Question 3042 Count Prefix and Suffix Pairs I

### Attempt 1: Use a helper function to check if it is prefix and suffix
```java
class Solution {
    public int countPrefixSuffixPairs(String[] words) {
        int count = 0;

        for (int i = 0; i < words.length - 1; i++) {
            for (int j = i + 1; j < words.length; j++) {
                if (isPrefixAndSuffix(words[i], words[j])) {
                    count++;
                }
            }
        }

        return count;
    }

    private boolean isPrefixAndSuffix(String str1, String str2) {
        int size1 = str1.length();
        int size2 = str2.length();

        if (size2 < size1) {
            return false;
        }

        for (int i = 0; i < size1; i++) {
            char ch = str1.charAt(i);
            if (ch != str2.charAt(i)) {
                return false;
            }
            if (ch != str2.charAt(size2 - size1 + i)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 99.50%)
- Memory: 42.22 MB (Beats: 50.19%)

<br>
