# [LeetCode Records](../../README.md) - Question 443 String Compression

### Attempt 1: Store the characters and its count in the ArrayList
```java
class Solution {
    public int compress(char[] chars) {
        List<Character> list = new ArrayList<>();
        int currCount = 1;
        for (int i = 1; i < chars.length; i++) {
            if (chars[i - 1] != chars[i]) {
                if (currCount == 1) {
                    list.addLast(chars[i - 1]);
                } else {
                    list.addLast(chars[i - 1]);
                    addDigitCount(currCount, list);
                    currCount = 1;
                }
            } else {
                currCount++;
            }
        }
        
        if (currCount == 1) {
            list.addLast(chars[chars.length - 1]);
        } else {
            list.addLast(chars[chars.length - 1]);
            addDigitCount(currCount, list);
        }

        int size = list.size();
        for (int i = 0; i < size; i++) {
            chars[i] = list.get(i);
        }

        return size;
    }

    private void addDigitCount(int n, List<Character> list) {
        List<Character> digits = new ArrayList<>();
        while (n > 0) {
            digits.addFirst((char)(n % 10 + '0'));
            n /= 10;
        }

        for (char digit : digits) {
            list.addLast(digit);
        }
    }
}
```
- Runtime: 2 ms (Beats: 35.16%)
- Memory: 43.73 MB (Beats: 78.92%)

<br>
