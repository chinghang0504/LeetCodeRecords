# [LeetCode Records](../../README.md) - Question 609 Find Duplicate File in System

### Attempt 1: Use a HashMap to store the content and its paths key-value pairs
```java
class Solution {
    public List<List<String>> findDuplicate(String[] paths) {
        Map<String, List<String>> contentToPathsMap = new HashMap<>();
        for (String path : paths) {
            String[] splits = path.split("\s");
            for (int i = 1; i < splits.length; i++) {
                int startIndex = splits[i].indexOf('(');
                int endIndex = splits[i].length();
                String fileName = splits[i].substring(0, startIndex);
                String content = splits[i].substring(startIndex + 1, endIndex);

                List<String> list = contentToPathsMap.get(content);
                if (list == null) {
                    list = new ArrayList<>();
                    contentToPathsMap.put(content, list);
                }
                list.add(splits[0] + "/" + fileName);
            }
        }

        List<List<String>> ans = new ArrayList<>();
        for (List<String> list : contentToPathsMap.values()) {
            if (list.size() > 1) {
                ans.add(list);
            }
        }

        return ans;
    }
}
```
- Runtime: 19 ms (Beats: 93.31%)
- Memory: 53.21 MB (Beats: 65.99%)

<br>

### Attempt 2: Use StringBuilder to improve the efficiency
```java
class Solution {
    public List<List<String>> findDuplicate(String[] paths) {
        Map<String, List<String>> contentToPathsMap = new HashMap<>();
        for (String path : paths) {
            String[] splits = path.split("\s");
            for (int i = 1; i < splits.length; i++) {
                int startIndex = splits[i].indexOf('(');
                int endIndex = splits[i].length();
                String fileName = splits[i].substring(0, startIndex);
                String content = splits[i].substring(startIndex + 1, endIndex);

                StringBuilder stringBuilder = new StringBuilder();
                stringBuilder.append(splits[0]);
                stringBuilder.append('/');
                stringBuilder.append(fileName);

                List<String> list = contentToPathsMap.get(content);
                if (list == null) {
                    list = new ArrayList<>();
                    contentToPathsMap.put(content, list);
                }
                list.add(stringBuilder.toString());
            }
        }

        List<List<String>> ans = new ArrayList<>();
        for (List<String> list : contentToPathsMap.values()) {
            if (list.size() > 1) {
                ans.add(list);
            }
        }

        return ans;
    }
}
```
- Runtime: 15 ms (Beats: 97.67%)
- Memory: 53.81 MB (Beats: 30.81%)

<br>
