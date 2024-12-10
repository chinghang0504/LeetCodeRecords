# [LeetCode Records](../../README.md) - Question 1023 Camelcase Matching

### Attempt 1: Use two indices to track the current characters on both array
```java
class Solution {
    public List<Boolean> camelMatch(String[] queries, String pattern) {
        char[] patternArr = pattern.toCharArray();
        List<Boolean> ans = new ArrayList<>();

        for (String query : queries) {
            ans.add(isMatched(patternArr, query.toCharArray()));
        }

        return ans;
    }

    private boolean isMatched(char[] patternArr, char[] queryArr) {
        int patternIndex = 0;
        int queryIndex = 0;
        
        while (patternIndex < patternArr.length && queryIndex < queryArr.length) {
            if (patternArr[patternIndex] == queryArr[queryIndex]) {
                patternIndex++;
            } else if (Character.isUpperCase(queryArr[queryIndex])) {
                return false;
            }

            queryIndex++;
        }

        while (queryIndex < queryArr.length && Character.isLowerCase(queryArr[queryIndex])) {
            queryIndex++;
        }

        return patternIndex == patternArr.length && queryIndex == queryArr.length;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.40 MB (Beats: 77.36%)

<br>
