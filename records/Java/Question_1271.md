# [LeetCode Records](../../README.md) - Question 1271 Hexspeak

### Attempt 1: Use Long.valueOf() to convert a string to a Long integer
```java
class Solution {
    public String toHexspeak(String num) {
        Long val = Long.valueOf(num);
        int[] arr = new int[12];
        int size = 0;

        while (val > 0) {
            arr[size] = (int) (val % 16);
            val /= 16;
            size++;
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < size; i++) {
            char ch = 'O';
            switch (arr[i]) {
                case 0:
                    ch = 'O';
                    break;
                case 1:
                    ch = 'I';
                    break;
                case 10:
                    ch = 'A';
                    break;
                case 11:
                    ch = 'B';
                    break;
                case 12:
                    ch = 'C';
                    break;
                case 13:
                    ch = 'D';
                    break;
                case 14:
                    ch = 'E';
                    break;
                case 15:
                    ch = 'F';
                    break;
                default:
                    return "ERROR";
            }
            stringBuilder.append(ch);
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 2 ms (Beats: 80.56%)
- Memory: 42.26 MB (Beats: 25.00%)

<br>
