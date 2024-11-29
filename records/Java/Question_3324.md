# [LeetCode Records](../../README.md) - Question 3324 Find the Sequence of Strings Appeared on the Screen

### Attempt 1: Use a loop until the current string is the same as the target
```java
class Solution {
    public List<String> stringSequence(String target) {
        char[] arr = target.toCharArray();
        List<String> ans = new ArrayList<>();

        String currStr = "a";
        ans.add(currStr);

        int currIndex = 0;
        while (!currStr.equals(target)) {
            char ch = currStr.charAt(currIndex);
            if (ch < arr[currIndex]) {
                currStr = currStr.substring(0, currIndex) + (char)(ch + 1);
                ans.add(currStr);
            } else {
                currStr += 'a';
                ans.add(currStr);
                currIndex++;
            }
        }

        return ans;
    }
}
```
- Runtime: 15 ms (Beats: 15.03%)
- Memory: 55.42 MB (Beats: 77.67%)

<br>

### Attempt 2: Use a nested loop until reaching the same length
```java
class Solution {
    public List<String> stringSequence(String target) {
        char[] arr = target.toCharArray();
        List<String> ans = new ArrayList<>();

        String currStr = "";
        for (int i = 0; i < arr.length; i++) {
            char ch = 'a';
            while (ch < arr[i]) {
                ans.add(currStr + ch);
                ch++;
            }
            currStr += ch;
            ans.add(currStr);
        }

        return ans;
    }
}
```
- Runtime: 11 ms (Beats: 38.14%)
- Memory: 55.38 MB (Beats: 89.72%)

<br>

### Attempt 3: Use StringBuilder to create a template of the string
```java
class Solution {
    public List<String> stringSequence(String target) {
        char[] arr = target.toCharArray();
        List<String> ans = new ArrayList<>();

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < arr.length; i++) {
            char ch = 'a';
            stringBuilder.append(ch);
            ans.add(stringBuilder.toString());
            ch++;

            while (ch <= arr[i]) {
                stringBuilder.setCharAt(i, ch);
                ans.add(stringBuilder.toString());
                ch++;
            }
        }

        return ans;
    }
}
```
- Runtime: 5 ms (Beats: 100.00%)
- Memory: 55.73 MB (Beats: 30.58%)

<br>
