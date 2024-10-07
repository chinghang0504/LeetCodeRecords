# [LeetCode Records](../../README.md) - Question 1807 Evaluate the Bracket Pairs of a String

### Attempt 1: Use a HashMap to store the knowledge key-value pairs
```java
class Solution {
    public String evaluate(String s, List<List<String>> knowledge) {
        Map<String, String> map = new HashMap<>();
        for (List<String> item : knowledge) {
            map.put(item.get(0), item.get(1));
        }
        
        char[] arr = s.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();
        int i = 0;
        while (i < arr.length) {
            if (arr[i] == '(') {
                int j = i + 1;
                while (arr[j] != ')') {
                    j++;
                }

                String key = s.substring(i + 1, j);
                String value = map.get(key);
                if (value == null) {
                    stringBuilder.append('?');
                } else {
                    stringBuilder.append(value);
                }

                i = j + 1;
            } else {
                stringBuilder.append(arr[i]);
                i++;
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 33 ms (Beats: 91.04%)
- Memory: 83.62 MB (Beats: 77.61%)

<br>
