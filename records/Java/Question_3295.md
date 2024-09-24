# [LeetCode Records](../../README.md) - Question 3295 Report Spam Message

### Attempt 1: Use a HashSet to store banned words
```java
class Solution {
    public boolean reportSpam(String[] message, String[] bannedWords) {
        Set<String> set = new HashSet<>();
        for (String bannedWord : bannedWords) {
            set.add(bannedWord);
        }

        int count = 0;
        for (String str : message) {
            if (set.contains(str)) {
                count++;

                if (count >= 2) {
                    return true;
                }
            }
        }

        return false;
    }
}
```
- Runtime: 49 ms (Beats: 91.20%)
- Memory: 74.01 MB (Beats: 34.25%)

<br>
