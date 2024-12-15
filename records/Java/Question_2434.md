# [LeetCode Records](../../README.md) - Question 2434 Using a Robot to Print the Lexicographically Smallest String

### Attempt 1: Find the minimum value of the character in string s
```java
class Solution {
    public String robotWithString(String s) {
        StringBuilder stringBuilder = new StringBuilder();
        List<Character> tList = new ArrayList<>();

        while (!s.isEmpty()) {
            char[] arr = s.toCharArray();

            char minCh = arr[0];
            int minChLastIndex = 0;
            for (int i = 1; i < arr.length; i++) {
                if (arr[i] < minCh) {
                    minCh = arr[i];
                    minChLastIndex = i;
                } else if (arr[i] == minCh) {
                    minChLastIndex = i;
                }
            }

            while (!tList.isEmpty() && tList.getLast() <= minCh) {
                stringBuilder.append(tList.removeLast());
            }

            for (int i = 0; i <= minChLastIndex; i++) {
                if (arr[i] == minCh) {
                    stringBuilder.append(arr[i]);
                } else {
                    tList.addLast(arr[i]);
                }
            }

            s = s.substring(minChLastIndex + 1);
        }

        StringBuilder secondPart = new StringBuilder();
        for (char ch : tList) {
            secondPart.append(ch);
        }
        stringBuilder.append(secondPart.reverse().toString());

        return stringBuilder.toString();
    }
}
```
- Runtime: 42 ms (Beats: 90.00%)
- Memory: 47.90 MB (Beats: 81.52%)

<br>
