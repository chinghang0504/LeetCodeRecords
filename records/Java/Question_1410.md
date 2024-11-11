# [LeetCode Records](../../README.md) - Question 1410 HTML Entity Parser

### Attempt 1: Use nested if-else statements to check the special characters
```java
class Solution {
    public String entityParser(String text) {
        char[] arr = text.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();

        int i = 0;
        while (i < arr.length) {
            if (arr[i] == '&') {
                boolean isSpecial = false;

                if (i + 3 < arr.length && arr[i + 3] == ';') {
                    if (arr[i + 1] == 'g' && arr[i + 2] == 't') {
                        stringBuilder.append('>');
                        i += 4;
                        isSpecial = true;
                    } else if (arr[i + 1] == 'l' && arr[i + 2] == 't') {
                        stringBuilder.append('<');
                        i += 4;
                        isSpecial = true;
                    }
                } else if (i + 4 < arr.length && arr[i + 4] == ';') {
                    if (arr[i + 1] == 'a' && arr[i + 2] == 'm' && arr[i + 3] == 'p') {
                        stringBuilder.append('&');
                        i += 5;
                        isSpecial = true;
                    }
                } else if (i + 5 < arr.length && arr[i + 5] == ';') {
                    if (arr[i + 1] == 'q' && arr[i + 2] == 'u' && arr[i + 3] == 'o' && arr[i + 4] == 't') {
                        stringBuilder.append('\"');
                        i += 6;
                        isSpecial = true;
                    } else if (arr[i + 1] == 'a' && arr[i + 2] == 'p' && arr[i + 3] == 'o' && arr[i + 4] == 's') {
                        stringBuilder.append('\'');
                        i += 6;
                        isSpecial = true;
                    }
                } else if (i + 6 < arr.length && arr[i + 6] == ';') {
                    if (arr[i + 1] == 'f' && arr[i + 2] == 'r' && arr[i + 3] == 'a' && arr[i + 4] == 's' && arr[i + 5] == 'l') {
                        stringBuilder.append('/');
                        i += 7;
                        isSpecial = true;
                    }
                }

                if (!isSpecial) {
                    stringBuilder.append(arr[i]);
                    i++;
                }
            } else {
                stringBuilder.append(arr[i]);
                i++;
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 10 ms (Beats: 100.00%)
- Memory: 45.46 MB (Beats: 53.21%)

<br>
