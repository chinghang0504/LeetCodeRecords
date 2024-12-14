# [LeetCode Records](../../README.md) - Question 2284 Sender With Largest Word Count

### Attempt 1: Use split() to get the number of words
```java
class Solution {
    public String largestWordCount(String[] messages, String[] senders) {
        Map<String, Integer> map = new HashMap<>();

        for (int i = 0; i < messages.length; i++) {
            int num = messages[i].split("\s").length;
            map.merge(senders[i], num, Integer::sum);
        }

        String maxName = "";
        int maxNum = 0;
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            int num = entry.getValue();
            if (num > maxNum) {
                maxNum = num;
                maxName = entry.getKey();
            } else if (num == maxNum) {
                String name = entry.getKey();
                if (name.compareTo(maxName) > 0) {
                    maxName = name;
                }
            }
        }

        return maxName;
    }
}
```
- Runtime: 52 ms (Beats: 53.15%)
- Memory: 54.96 MB (Beats: 34.68%)

<br>

### Attempt 2: Count the number of space characters to get the number of words
```java
class Solution {
    public String largestWordCount(String[] messages, String[] senders) {
        Map<String, Integer> map = new HashMap<>();

        for (int i = 0; i < messages.length; i++) {
            int num = 1;
            for (char ch : messages[i].toCharArray()) {
                if (ch == ' ') {
                    num++;
                }
            }
            map.merge(senders[i], num, Integer::sum);
        }

        String maxName = "";
        int maxNum = 0;
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            int num = entry.getValue();
            if (num > maxNum) {
                maxNum = num;
                maxName = entry.getKey();
            } else if (num == maxNum) {
                String name = entry.getKey();
                if (name.compareTo(maxName) > 0) {
                    maxName = name;
                }
            }
        }

        return maxName;
    }
}
```
- Runtime: 21 ms (Beats: 94.76%)
- Memory: 51.64 MB (Beats: 75.08%)

<br>
