# [LeetCode Records](../../README.md) - Question 3227 Vowels Game in a String

### Attempt 1: Use toCharArray() to count the number of vowels
```java
class Solution {
    public boolean doesAliceWin(String s) {
        int count = 0;
        for (char ch : s.toCharArray()) {
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
                count++;
            }
        }

        return count != 0;
    }
}
```
- Runtime: 7 ms (Beats: 59.97%)
- Memory: 45.23 MB (Beats: 81.29%)

<br>

### Attempt 2: Use charAt() to count the number of vowels
```java
class Solution {
    public boolean doesAliceWin(String s) {
        int count = 0;
        int size = s.length();
        for (int i = 0; i < size; i++) {
            char ch = s.charAt(i);
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
                count++;
            }
        }

        return count != 0;
    }
}
```
- Runtime: 6 ms (Beats: 66.85%)
- Memory: 45.34 MB (Beats: 66.85%)

<br>
