# [LeetCode Records](../../README.md) - Question 937 Reorder Data in Log Files

### Attempt 1: Store the original logs, the identifiers, and the contents
```java
class Solution {
    public String[] reorderLogFiles(String[] logs) {
        List<String[]> letterLogs = new ArrayList<>();
        List<String> digitLogs = new ArrayList<>();

        for (String log : logs) {
            int len = log.length();
            char lastCh = log.charAt(len - 1);
            if (Character.isDigit(lastCh)) {
                digitLogs.add(log);
            } else {
                int spaceIndex = log.indexOf(' ');
                letterLogs.add(new String[]{ log, log.substring(0, spaceIndex), log.substring(spaceIndex + 1, len)});
            }
        }

        letterLogs.sort((log1, log2) -> {
            if (!log1[2].equals(log2[2])) {
                return log1[2].compareTo(log2[2]);
            } else {
                return log1[1].compareTo(log2[1]);
            }
        });

        String[] ans = new String[logs.length];
        int index = 0;
        for (String[] item : letterLogs) {
            ans[index] = item[0];
            index++;
        }
        for (String item : digitLogs) {
            ans[index] = item;
            index++;
        }

        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.46 MB (Beats: 88.17%)

<br>
