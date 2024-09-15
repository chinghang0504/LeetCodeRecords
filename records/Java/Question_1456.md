# [LeetCode Records](../../README.md) - Question 1456 Maximum Number of Vowels in a Substring of Given Length

### Attempt 1: Use a for loop that searches from the start to the end
```java
class Solution {
    public int maxVowels(String s, int k) {
        char[] arr = s.toCharArray();

        int currCount = 0;
        for (int i = 0; i < k; i++) {
            if (isVowel(arr[i])) {
                currCount++;
            }
        }

        int maxCount = currCount;
        for (int i = k; i < arr.length; i++) {
            if (isVowel(arr[i])) {
                currCount++;
            }
            if (isVowel(arr[i - k])) {
                currCount--;
            }

            maxCount = Math.max(maxCount, currCount);
        }

        return maxCount;
    }

    private boolean isVowel(char ch) {
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
    }
}
```
- Runtime: 10 ms (Beats: 92.87%)
- Memory: 45.15 MB (Beats: 13.53%)

<br>
