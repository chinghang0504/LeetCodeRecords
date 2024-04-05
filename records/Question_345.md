# [LeetCode Records](../README.md) - Question 345 Reverse Vowels of a String

### Attempt 1: Create a char array first
```java
class Solution {
    public String reverseVowels(String s) {
        char[] str = s.toCharArray();

        int i = 0;
        int j = str.length - 1;
        while (true) {
            while (i < j && !isVowel(str[i])) {
                i++;
            }
            while (i < j && !isVowel(str[j])) {
                j--;
            }

            if (i >= j) {
                break;
            } else {
                char ch = str[i];
                str[i] = str[j];
                str[j] = ch;
                i++;
                j--;
            }
        }

        return String.valueOf(str);
    }

    private boolean isVowel(char ch) {
        return switch (ch) {
            case 'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U' -> true;
            default -> false;
        };
    }
}
```
- Runtime: 2 ms (Beats: 98.84%)
- Memory: 44.49 MB (Beats: 91.96%)

<br>

### Attempt 2: Add a boolean array to replace a function
```java
import java.util.Arrays;
import java.util.Map;

class Solution {
    public String reverseVowels(String s) {
        boolean[] vowles = new boolean[128];
        vowles['a'] = true;
        vowles['e'] = true;
        vowles['i'] = true;
        vowles['o'] = true;
        vowles['u'] = true;
        vowles['A'] = true;
        vowles['E'] = true;
        vowles['I'] = true;
        vowles['O'] = true;
        vowles['U'] = true;
        
        char[] str = s.toCharArray();
        int i = 0;
        int j = str.length - 1;
        
        while (true) {
            while (i < str.length && !vowles[str[i]]) {
                i++;
            }
            while (j >= 0 && !vowles[str[j]]) {
                j--;
            }

            if (i >= j) {
                break;
            } else {
                char ch = str[i];
                str[i] = str[j];
                str[j] = ch;
                i++;
                j--;
            }
        }

        return String.valueOf(str);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.12 MB (Beats: 27.13%)

<br>
