# [LeetCode Records](../README.md) - Question 13 Roman to Integer

### Attempt 1: Use Map
```java
class Solution {
    Map<Character, Integer> symbols = Map.of('I', 1, 'V', 5, 'X', 10, 'L', 50, 'C', 100, 'D', 500, 'M', 1000);
    
    public int romanToInt(String s) {
        int value = 0;

        for (int i = 0; i < s.length(); i++) {
            int val1 = symbols.get(s.charAt(i));

            if (i + 1 < s.length()) {
                int val2 = symbols.get(s.charAt(i + 1));
                if (val1 < val2) {
                    value -= val1;
                } else {
                    value += val1;
                }
            } else {
                value += val1;
            }
        }

        return value;
    }
}
```
- Runtime: 6 ms (Beats: 32.41%)
- Memory: 44.73 MB (Beats: 39.43%)

<br>

### Attempt 2: Use an array
```java
class Solution {
    public int romanToInt(String s) {
        int[] symbols = new int[128];
        symbols['I'] = 1;
        symbols['V'] = 5;
        symbols['X'] = 10;
        symbols['L'] = 50;
        symbols['C'] = 100;
        symbols['D'] = 500;
        symbols['M'] = 1000;

        int value = 0;

        for (int i = 0; i < s.length(); i++) {
            int val1 = symbols[s.charAt(i)];

            if (i + 1 < s.length()) {
                int val2 = symbols[s.charAt(i + 1)];
                if (val1 < val2) {
                    value -= val1;
                } else {
                    value += val1;
                }
            } else {
                value += val1;
            }
        }

        return value;
    }
}
```
- Runtime: 3 ms (Beats: 83.14%)
- Memory: 44.62 MB (Beats: 53.08%)

<br>

### Attempt 3: Use a switch
```java
class Solution {
    public int romanToInt(String s) {
        int value = 0;

        for (int i = 0; i < s.length(); i++) {
            int val1 = convert(s.charAt(i));

            if (i + 1 < s.length()) {
                int val2 = convert(s.charAt(i + 1));
                if (val1 < val2) {
                    value -= val1;
                } else {
                    value += val1;
                }
            } else {
                value += val1;
            }
        }

        return value;
    }

    private int convert(char ch) {
        return switch (ch) {
            case 'I' -> 1;
            case 'V' -> 5;
            case 'X' -> 10;
            case 'L' -> 50;
            case 'C' -> 100;
            case 'D' -> 500;
            case 'M' -> 1000;
            default -> 0;
        };
    }
}
```
- Runtime: 3 ms (Beats: 83.14%)
- Memory: 45.04 MB (Beats: 14.24%)

<br>

### Attempt 4: Use a switch and reduce a if-else statment in the loop
```java
class Solution {
    public int romanToInt(String s) {
        int value = 0;
        int val1 = convert(s.charAt(0));

        for (int i = 1; i < s.length(); i++) {
            int val2 = convert(s.charAt(i));
            value = val1 < val2 ? value - val1 : value + val1;
            val1 = val2;
        }
        value += val1;

        return value;
    }

    private int convert(char ch) {
        return switch (ch) {
            case 'I' -> 1;
            case 'V' -> 5;
            case 'X' -> 10;
            case 'L' -> 50;
            case 'C' -> 100;
            case 'D' -> 500;
            case 'M' -> 1000;
            default -> 0;
        };
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.50 MB (Beats: 68.11%)

<br>
