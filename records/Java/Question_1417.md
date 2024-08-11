# [LeetCode Records](../../README.md) - Question 1417 Reformat The String

### Attempt 1: Use two ArrayList to store the characters
```java
class Solution {
    public String reformat(String s) {
        char[] arr = s.toCharArray();
        List<Character> digitList = new ArrayList<>();
        List<Character> letterList = new ArrayList<>();

        for (char ch : arr) {
            if (ch >= 'a') {
                letterList.add(ch);
            } else {
                digitList.add(ch);
            }
        }

        int digitCount = digitList.size();
        int letterCount = letterList.size();
        if (Math.abs(digitCount - letterCount) > 1) {
            return "";
        }

        char[] answer = new char[arr.length];
        List<Character> list1 = null;
        List<Character> list2 = null;
        if (digitCount >= letterCount) {
            list1 = digitList;
            list2 = letterList;
        } else {
            list1 = letterList;
            list2 = digitList;
        }

        int i = 0;
        for (char ch : list1) {
            answer[i] = ch;
            i += 2;
        }

        i = 1;
        for (char ch : list2) {
            answer[i] = ch;
            i += 2;
        }

        return new String(answer);
    }
}
```
- Runtime: 3 ms (Beats: 83.33%)
- Memory: 44.73 MB (Beats: 24.11%)

<br>
