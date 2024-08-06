# [LeetCode Records](../../README.md) - Question 1180 Count Substrings with Only One Distinct Letter

### Attempt 1: Use a for loop to get the maximum lengths of the same character arrays
```java
class Solution {
    public int countLetters(String s) {
        char[] arr = s.toCharArray();
        int totalCount = 0;
        int count = 1;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] == arr[i - 1]) {
                count++;
            } else {
                totalCount += getNumberOfSubstrings(count);
                count = 1;
            }
        }
        totalCount += getNumberOfSubstrings(count);

        return totalCount;
    }

    private int getNumberOfSubstrings(int n) {
        return (1 + n) * n / 2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.28 MB (Beats: 53.76%)

<br>
