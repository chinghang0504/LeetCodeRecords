# [LeetCode Records](../../README.md) - Question 567 Permutation in String

### Attempt 1: Use an int[] to store the character counts for each substring
```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        if (arr1.length > arr2.length) {
            return false;
        }

        int[] counts1 = new int[26];
        int[] counts2 = new int[26];
        for (int i = 0; i < arr1.length; i++) {
            counts1[arr1[i] - 'a']++;
            counts2[arr2[i] - 'a']++;
        }
        if (isEqual(counts1, counts2)) {
            return true;
        }

        for (int i = arr1.length; i < arr2.length; i++) {
            counts2[arr2[i] - 'a']++;
            counts2[arr2[i - arr1.length] - 'a']--;
            if (isEqual(counts1, counts2)) {
                return true;
            }
        }
        
        return false;
    }

    private boolean isEqual(int[] counts1, int[] counts2) {
        for (int i = 0; i < 26; i++) {
            if (counts1[i] != counts2[i]) {
                return false;
            }
        }
        return true;
    }
}
```
- Runtime: 4 ms (Beats: 99.16%)
- Memory: 42.57 MB (Beats: 76.47%)

<br>
