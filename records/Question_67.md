# [LeetCode Records](../README.md) - Question 67 Add Binary

### Attempt 1: Loop from backward
```java
class Solution {
    StringBuilder stringBuilder = new StringBuilder();
    int plusOne = 0;

    public String addBinary(String a, String b) {
        int i = a.length() - 1, j = b.length() - 1;

        for (; i >= 0 && j >= 0; i--, j--) {
            int value = plusOne;
            if (a.charAt(i) == '1') {
                value += 1;
            }
            if (b.charAt(j) == '1') {
                value += 1;
            }
            addCharacter(value);
        }
        for (; i >= 0; i--) {
            int value = plusOne;
            if (a.charAt(i) == '1') {
                value += 1;
            }
            addCharacter(value);
        }
        for (; j >= 0; j--) {
            int value = plusOne;
            if (b.charAt(j) == '1') {
                value += 1;
            }

            addCharacter(value);
        }

        if (plusOne == 1) {
            stringBuilder.append('1');
        }

        return stringBuilder.reverse().toString();
    }

    void addCharacter(int value) {
        switch (value) {
            case 0 -> {
                plusOne = 0;
                stringBuilder.append('0');
            }
            case 1 -> {
                plusOne = 0;
                stringBuilder.append('1');
            }
            case 2 -> {
                plusOne = 1;
                stringBuilder.append('0');
            }
            case 3 -> {
                plusOne = 1;
                stringBuilder.append('1');
            }
        }
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.24 MB (Beats: 45.08%)

<br>
