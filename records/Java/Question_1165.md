# [LeetCode Records](../../README.md) - Question 1165 Single-Row Keyboard

### Attempt 1: Use a HashMap to record the index of characters
```java
class Solution {
    public int calculateTime(String keyboard, String word) {
        Map<Character, Integer> map = new HashMap<>();
        char[] chars = keyboard.toCharArray();
        for (int i = 0; i < chars.length; i++) {
            map.put(chars[i], i);
        }

        int currIndex = 0;
        int sum = 0;
        for (char ch : word.toCharArray()) {
            int nextIndex = map.get(ch);
            sum += Math.abs(nextIndex - currIndex);
            currIndex = nextIndex;
        }

        return sum;
    }
}
```
- Runtime: 8 ms (Beats: 56.02%)
- Memory: 42.10 MB (Beats: 75.52%)

<br>
