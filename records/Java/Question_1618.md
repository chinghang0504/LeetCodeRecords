# [LeetCode Records](../../README.md) - Question 1618 Maximum Font to Fit a Sentence in a Screen

### Attempt 1: Use an int[] to count the number of characters
```java
/**
 * // This is the FontInfo's API interface.
 * // You should not implement it, or speculate about its implementation
 * interface FontInfo {
 *     // Return the width of char ch when fontSize is used.
 *     public int getWidth(int fontSize, char ch) {}
 *     // Return Height of any char when fontSize is used.
 *     public int getHeight(int fontSize)
 * }
 */
class Solution {
    public int maxFont(String text, int w, int h, int[] fonts, FontInfo fontInfo) {
        int[] counts = new int[26];
        for (char ch : text.toCharArray()) {
            counts[ch - 'a']++;
        }

        for (int i = 0; i < fonts.length; i++) {
            int height = fontInfo.getHeight(fonts[i]);
            if (height > h) {
                return i == 0 ? -1 : fonts[i - 1];
            }

            int sumOfWidth = 0;
            for (int j = 0; j < 26; j++) {
                if (counts[j] > 0) {
                    sumOfWidth += fontInfo.getWidth(fonts[i], (char)(j + 'a')) * counts[j];
                }
            }
            if (sumOfWidth > w) {
                return i == 0 ? -1 : fonts[i - 1];
            }
        }

        return fonts[fonts.length - 1];
    }
}
```
- Runtime: 3 ms (Beats: 80.00%)
- Memory: 55.22 MB (Beats: 57.14%)

<br>
