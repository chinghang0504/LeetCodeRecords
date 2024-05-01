# [LeetCode Records](../../README.md) - Question 10 Regular Expression Matching

### Attempt 1: Use recursion
```java
class Solution {
    public boolean isMatch(String s, String p) {
        return isMatchRecursion(s, p, 0, 0);
    }

    private boolean isMatchRecursion(String s, String p, int i, int j) {
        while (i < s.length() && j < p.length()) {
            char p1 = p.charAt(j);

            // The second character is '*'
            if (j + 1 < p.length() && p.charAt(j + 1) == '*') {
                for (int k = i; k < s.length(); k++) {
                    if (p1 == '.' || s.charAt(k) == p1) {
                        if (isMatchRecursion(s, p, k + 1, j+2)) {
                            return true;
                        }
                    } else {
                        break;
                    }
                }
                j += 2;
            }
            // The first character is '.' or matched
            else if (p1 == '.' || p1 == s.charAt(i)) {
                i++;
                j++;
            }
            // The first character does not match
            else {
                return false;
            }
        }

        if (i == s.length()) {
            if (j == p.length()) {
                return true;
            } else {
                for (int k = j; k < p.length(); k += 2) {
                    if (k + 1 >= p.length() || p.charAt(k + 1) != '*') {
                        return false;
                    }
                }
                return true;
            }
        } else {
            return false;
        }
    }
}
```
- Runtime: 279 ms (Beats: 23.18%)
- Memory: 41.90 MB (Beats: 62.33%)

<br>
