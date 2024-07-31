# [LeetCode Records](../../README.md) - Question 2299 Strong Password Checker II

### Attempt 1: Use a helper function that gets the type of a character
```java
class Solution {
    public boolean strongPasswordCheckerII(String password) {
        char[] arr = password.toCharArray();
        boolean hasLowerCase = false;
        boolean hasUpperCase = false;
        boolean hasDigit = false;
        boolean hasSpecial = false;

        if (arr.length < 8) {
            return false;
        }

        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] == arr[i + 1]) {
                return false;
            }
        }

        for (char ch : arr) {
            int type = getType(ch);
            if (type == 1) {
                hasLowerCase = true;
            } else if (type == 2) {
                hasUpperCase = true;
            } else if (type == 3) {
                hasDigit = true;
            } else if (type == 4) {
                hasSpecial = true;
            }
        }

        return hasLowerCase && hasUpperCase && hasDigit && hasSpecial;
    }

    private int getType(char ch) {
        if (Character.isLowerCase(ch)) {
            return 1;
        } else if (Character.isUpperCase(ch)) {
            return 2;
        } else if (Character.isDigit(ch)) {
            return 3;
        } else if ("!@#$%^&*()-+".indexOf(ch) != -1) {
            return 4;
        } else {
            return 0;
        }
    }
}
```
- Runtime: 1 ms (Beats: 86.25%)
- Memory: 40.55 MB (Beats: 99.63%)

<br>
