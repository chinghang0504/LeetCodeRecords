# [LeetCode Records](../../README.md) - Question 290 Word Pattern

### Attempt 1: Use two HashMap
```java
class Solution {
    public boolean wordPattern(String pattern, String s) {
        int size = pattern.length();
        String[] s_split = s.split(" ");
        if (size != s_split.length) {
            return false;
        }

        HashMap<Character, String> hashMap1 = new HashMap<>(26);
        HashMap<String, Character> hashMap2 = new HashMap<>(26);
        for (int i = 0; i < size; i++) {
            Character chKey = pattern.charAt(i);
            String strKey = s_split[i];

            String strValue = hashMap1.get(chKey);
            if (strValue == null) {
                if (hashMap2.get(strKey) == null) {
                    hashMap1.put(chKey, strKey);
                    hashMap2.put(strKey, chKey);
                } else {
                    return false;
                }
            } else if (!strValue.equals(strKey)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.15 MB (Beats: 74.27%)

<br>
