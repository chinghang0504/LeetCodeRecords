# [LeetCode Records](../../README.md) - Question 12 Integer to Roman

### Attempt 1: Use a huge if-else if-else statement
```java
class Solution {
    public String intToRoman(int num) {
        StringBuilder stringBuilder = new StringBuilder();

        while (num > 0) {
            if (num >= 1000) {
                stringBuilder.append('M');
                num -= 1000;
            } else if (num >= 900) {
                stringBuilder.append("CM");
                num -= 900;
            } else if (num >= 500) {
                stringBuilder.append('D');
                num -= 500;
            } else if (num >= 400) {
                stringBuilder.append("CD");
                num -= 400;
            } else if (num >= 100) {
                stringBuilder.append('C');
                num -= 100;
            } else if (num >= 90) {
                stringBuilder.append("XC");
                num -= 90;
            } else if (num >= 50) {
                stringBuilder.append('L');
                num -= 50;
            } else if (num >= 40) {
                stringBuilder.append("XL");
                num -= 40;
            } else if (num >= 10) {
                stringBuilder.append('X');
                num -= 10;
            } else if (num >= 9) {
                stringBuilder.append("IX");
                num -= 9;
            } else if (num >= 5) {
                stringBuilder.append('V');
                num -= 5;
            } else if (num >= 4) {
                stringBuilder.append("IV");
                num -= 4;
            } else {
                stringBuilder.append('I');
                num -= 1;
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.07 MB (Beats: 84.81%)

<br>

### Attempt 2: Use a for loop and two arrays to replace a huge if-else if-else statement
```java
class Solution {
    int[] nums = { 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };
    String[] symbols = { "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" };

    public String intToRoman(int num) {
        StringBuilder stringBuilder = new StringBuilder();

        while (num > 0) {
            for (int i = 0; i < nums.length; i++) {
                if (num >= nums[i]) {
                    num -= nums[i];
                    stringBuilder.append(symbols[i]);
                    break;
                }
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 3 ms (Beats: 97.67%)
- Memory: 44.37 MB (Beats: 57.47%)

<br>

### Attempt 3: Record i to avoid loop from start
```java
class Solution {
    int[] nums = { 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };
    String[] symbols = { "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" };

    public String intToRoman(int num) {
        StringBuilder stringBuilder = new StringBuilder();

        int i = 0;
        while (num > 0) {
            for (int j = i; j < nums.length; j++) {
                if (num >= nums[j]) {
                    num -= nums[j];
                    stringBuilder.append(symbols[j]);
                    if (j > i) {
                        i = j;
                    }
                    break;
                }
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 3 ms (Beats: 97.67%)
- Memory: 44.53 MB (Beats: 40.56%)

<br>
