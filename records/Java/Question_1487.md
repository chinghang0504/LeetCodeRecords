# [LeetCode Records](../../README.md) - Question 1487 Making File Names Unique

### Attempt 1: Use a HashSet to store the folder names and a HashMap to store the folder numbers
```java
class Solution {
    public String[] getFolderNames(String[] names) {
        Set<String> folderNames = new HashSet<>();
        Map<String, Integer> folderNumbers = new HashMap<>();
        String[] ans = new String[names.length];

        for (int i = 0; i < names.length; i++) {
            if (folderNames.contains(names[i])) {
                Integer number = folderNumbers.get(names[i]);
                if (number == null) {
                    number = 1;
                }
                
                StringBuilder stringBuilder = new StringBuilder();
                stringBuilder.append(names[i]);
                stringBuilder.append("(");
                stringBuilder.append(number);
                stringBuilder.append(")");
                String newFolderName = stringBuilder.toString();

                while (folderNames.contains(newFolderName)) {
                    number++;
                    stringBuilder = new StringBuilder();
                    stringBuilder.append(names[i]);
                    stringBuilder.append("(");
                    stringBuilder.append(number);
                    stringBuilder.append(")");
                    newFolderName = stringBuilder.toString();
                }

                ans[i] = newFolderName;
                folderNames.add(newFolderName);
                folderNumbers.put(names[i], number + 1);
            } else {
                ans[i] = names[i];
                folderNames.add(names[i]);
            }
        }

        return ans;
    }
}
```
- Runtime: 47 ms (Beats: 82.35%)
- Memory: 62.06 MB (Beats: 8.97%)

<br>
