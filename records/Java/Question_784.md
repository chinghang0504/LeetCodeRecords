# [LeetCode Records](../../README.md) - Question 784 Letter Case Permutation

### Attempt 1: Use an ArrayList to store the previous strings
```java
class Solution {
    public List<String> letterCasePermutation(String s) {
        List<String> list = new ArrayList<>();
        list.add("");

        for (char ch : s.toCharArray()) {
            List<String> nextList = new ArrayList<>();

            if (!Character.isLetter(ch)) {
                for (String str : list) {
                    nextList.add(str + ch);
                }
            } else {
                char lowerCh = Character.toLowerCase(ch);
                char upperCh = Character.toUpperCase(ch);
                for (String str : list) {
                    nextList.add(str + lowerCh);
                    nextList.add(str + upperCh);
                }
            }

            list = nextList;
        }

        return list;
    }
}
```
- Runtime: 12 ms (Beats: 12.68%)
- Memory: 45.65 MB (Beats: 23.22%)

<br>
