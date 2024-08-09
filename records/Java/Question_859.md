# [LeetCode Records](../../README.md) - Question 859 Buddy Strings

### Attempt 1: Use three while loops to get the different characters
```java
class Solution {
    public boolean buddyStrings(String s, String goal) {
        char[] arr1 = s.toCharArray();
        char[] arr2 = goal.toCharArray();

        if (arr1.length != arr2.length) {
            return false;
        }

        if (s.equals(goal)) {
            return hasRepeatedCharacter(arr1);
        }

        char ch1 = 0, ch2 = 1, ch3 = 2, ch4 = 3;

        int i = 0;
        while (i < arr1.length) {
            if (arr1[i] != arr2[i]) {
                ch1 = arr1[i];
                ch2 = arr2[i];
                i++;
                break;
            }
            i++;
        }
        
        while (i < arr1.length) {
            if (arr1[i] != arr2[i]) {
                ch3 = arr1[i];
                ch4 = arr2[i];
                i++;
                break;
            }
            i++;
        }
        
        while (i < arr1.length) {
            if (arr1[i] != arr2[i]) {
                return false;
            }
            i++;
        }

        return ch1 == ch4 && ch3 == ch2;
    }

    private boolean hasRepeatedCharacter(char[] arr) {
        boolean[] saved = new boolean[26];

        for (char ch : arr) {
            if (saved[ch - 'a']) {
                return true;
            } else {
                saved[ch - 'a'] = true;
            }
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.73 MB (Beats: 14.83%)

<br>
