# [LeetCode Records](../../README.md) - Question 2325 Decode the Message

### Attempt 1: Use a HashMap
```java
class Solution {
    public String decodeMessage(String key, String message) {
        Map<Character, Character> map = new HashMap<>();
        char currCh = 'a';

        for (char ch : key.toCharArray()) {
            if (ch != ' ' && !map.containsKey(ch)) {
                map.put(ch, currCh);
                currCh++;
            }

            if (currCh > 'z') {
                break;
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (char ch : message.toCharArray()) {
            if (ch == ' ') {
                stringBuilder.append(ch);
            } else {
                stringBuilder.append(map.get(ch));
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 5 ms (Beats: 87.46%)
- Memory: 44.14 MB (Beats: 35.49%)

<br>
