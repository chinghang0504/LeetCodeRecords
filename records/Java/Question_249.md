# [LeetCode Records](../../README.md) - Question 249 Group Shifted Strings

### Attempt 1: Use a HashMap to store the pattern and strings key-value pairs
```java
class Solution {
    public List<List<String>> groupStrings(String[] strings) {
        Map<String, List<String>> map = new HashMap<>();
        for (String string : strings) {
            char[] arr = string.toCharArray();
            int diff = arr[0] - 'a';

            String key = null;
            if (diff != 0) {
                StringBuilder stringBuilder = new StringBuilder();
                for (char ch : arr) {
                    char nextCh = (char) (ch - diff);
                    if (nextCh < 'a') {
                        nextCh += 26;
                    }
                    stringBuilder.append(nextCh);
                }
                key = stringBuilder.toString();
            } else {
                key = string;
            }

            List<String> list = map.get(key);
            if (list == null) {
                list = new ArrayList<>();
                map.put(key, list);
            }
            list.add(string);
        }

        return new ArrayList<>(map.values());
    }
}
```
- Runtime: 2 ms (Beats: 82.34%)
- Memory: 43.23 MB (Beats: 50.75%)

<br>
