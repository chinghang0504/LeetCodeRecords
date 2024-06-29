# [LeetCode Records](../../README.md) - Question 1773 Count Items Matching a Rule

### Attempt 1: Use a loop with switch statement
```java
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
        int count = 0;

        for (List<String> item : items) {
            String value = "";
            switch (ruleKey) {
                case "type":
                    value = item.get(0);
                    break;
                case "color":
                    value = item.get(1);
                    break;
                case "name":
                    value = item.get(2);
                    break;
            }
            if (value.equals(ruleValue)) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 34.28%)
- Memory: 51.00 MB (Beats: 9.43%)

<br>

### Attempt 2: Use if statement with a loop
```java
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
        int count = 0;

        if (ruleKey.equals("type")) {
            for (List<String> item : items) {
                if (item.get(0).equals(ruleValue)) {
                    count++;
                }
            }
        } else if (ruleKey.equals("color")) {
            for (List<String> item : items) {
                if (item.get(1).equals(ruleValue)) {
                    count++;
                }
            }
        } else if (ruleKey.equals("name")) {
            for (List<String> item : items) {
                if (item.get(2).equals(ruleValue)) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 98.86%)
- Memory: 50.60 MB (Beats: 27.99%)

<br>
