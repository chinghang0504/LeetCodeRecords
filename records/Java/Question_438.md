# [LeetCode Records](../../README.md) - Question 438 Find All Anagrams in a String

### Attempt 1: Use an int[] to store the character counts for each substring
```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        char[] arr1 = s.toCharArray();
        char[] arr2 = p.toCharArray();
        if (arr1.length < arr2.length) {
            return List.of();
        }

        int[] counts1 = new int[26];
        int[] counts2 = new int[26];
        List<Integer> ans = new ArrayList<>();
        for (char ch : arr2) {
            counts2[ch - 'a']++;
        }
        for (int i = 0; i < arr2.length; i++) {
            counts1[arr1[i] - 'a']++;
        }
        if (isEqual(counts1, counts2)) {
            ans.add(0);
        }

        for (int i = arr2.length; i < arr1.length; i++) {
            counts1[arr1[i] - 'a']++;
            counts1[arr1[i - arr2.length] - 'a']--;

            if (isEqual(counts1, counts2)) {
                ans.add(i - arr2.length + 1);
            }
        }

        return ans;
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
- Runtime: 6 ms (Beats: 97.85%)
- Memory: 44.09 MB (Beats: 99.71%)

<br>
