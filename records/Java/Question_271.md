# [LeetCode Records](../../README.md) - Question 271 Encode and Decode Strings

### Attempt 1: Use a special pattern that stores the length of the string and the original string
```java
public class Codec {

    // Encodes a list of strings to a single string.
    public String encode(List<String> strs) {
        StringBuilder stringBuilder = new StringBuilder();

        for (String str : strs) {
            stringBuilder.append(str.length());
            stringBuilder.append(' ');
            stringBuilder.append(str);
        }

        return stringBuilder.toString();
    }

    // Decodes a single string to a list of strings.
    public List<String> decode(String s) {
        int len = s.length();
        List<String> ans = new ArrayList<>();

        int i = 0;
        while (i < len) {
            int wordLen = 0;
            char ch = s.charAt(i);
            while (ch != ' ') {
                wordLen = wordLen * 10 + ch - '0';
                i++;
                ch = s.charAt(i);
            }
            i++;

            ans.add(s.substring(i, i + wordLen));
            i = i + wordLen;
        }

        return ans;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec codec = new Codec();
// codec.decode(codec.encode(strs));
```
- Runtime: 3 ms (Beats: 99.10%)
- Memory: 45.46 MB (Beats: 67.35%)

<br>
