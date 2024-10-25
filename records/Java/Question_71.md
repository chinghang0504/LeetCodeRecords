# [LeetCode Records](../../README.md) - Question 71 Simplify Path

### Attempt 1: Use split() to split the parts of a path
```java
class Solution {
    public String simplifyPath(String path) {
        String[] splits = path.split("/");

        List<String> list = new ArrayList<>();
        for (int i = 0; i < splits.length; i++) {
            if (splits[i].isEmpty() || splits[i].equals(".")) {
                continue;
            } else if (splits[i].equals("..")) {
                if (!list.isEmpty()) {
                    list.removeLast();
                }
            } else {
                list.add(splits[i]);
            }
        }

        if (list.size() == 0) {
            return "/";
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (String item : list) {
            stringBuilder.append("/");
            stringBuilder.append(item);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 3 ms (Beats: 98.39%)
- Memory: 42.89 MB (Beats: 95.55%)

<br>
