# [LeetCode Records](../../README.md) - Question 383 Ransom Note

### Attempt 1: Use an int array to record the character counts
```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] saved = new int[26];
        int magazineSize = magazine.length();
        for (int i = 0; i < magazineSize; i++) {
            saved[magazine.charAt(i) - 'a']++;
        }

        int ransomNoteSize = ransomNote.length();
        for (int i = 0; i < ransomNoteSize; i++) {
            int index = ransomNote.charAt(i) - 'a';
            saved[index]--;
            if (saved[index] < 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 99.17%)
- Memory: 44.43 MB (Beats: 82.94%)

<br>
