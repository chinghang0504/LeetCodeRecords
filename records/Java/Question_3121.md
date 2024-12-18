# [LeetCode Records](../../README.md) - Question 3121 Count the Number of Special Characters II

### Attempt 1: Use an int[] to store the last index of each lowercase letter and an int[] to store the first index of each uppercase letter
```java
class Solution {
    public int numberOfSpecialChars(String word) {
        int[] lowerCases = new int[26];
        int[] upperCases = new int[26];
        char[] arr = word.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            if (Character.isLowerCase(arr[i])) {
                lowerCases[arr[i] - 'a'] = i + 1;
            } else if (upperCases[arr[i] - 'A'] == 0) {
                upperCases[arr[i] - 'A'] = i + 1;
            }
        }

        int count = 0;
        for (int i = 0; i < 26; i++) {
            if (lowerCases[i] != 0 && upperCases[i] != 0 && lowerCases[i] < upperCases[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 21 ms (Beats: 75.11%)
- Memory: 45.33 MB (Beats: 97.47%)

<br>

### Attempt 2: Without using Character.isLowerCase()
```java
class Solution {
    public int numberOfSpecialChars(String word) {
        int[] lowerCases = new int[26];
        int[] upperCases = new int[26];
        char[] arr = word.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] >= 'a' && arr[i] <= 'z') {
                lowerCases[arr[i] - 'a'] = i + 1;
            } else if (upperCases[arr[i] - 'A'] == 0) {
                upperCases[arr[i] - 'A'] = i + 1;
            }
        }

        int count = 0;
        for (int i = 0; i < 26; i++) {
            if (lowerCases[i] != 0 && upperCases[i] != 0 && lowerCases[i] < upperCases[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 8 ms (Beats: 98.31%)
- Memory: 45.65 MB (Beats: 86.08%)

<br>
