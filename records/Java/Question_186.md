# [LeetCode Records](../../README.md) - Question 186 Reverse Words in a String II

### Attempt 1: Use an ArrayList to store the start index and end index of each word
```java
class Solution {
    public void reverseWords(char[] s) {
        List<int[]> list = new ArrayList<>();

        int currStart = 0;
        for (int i = 1; i < s.length; i++) {
            if (s[i] == ' ') {
                list.addFirst(new int[]{ currStart, i });
                currStart = i + 1;
            }
        }
        list.addFirst(new int[]{ currStart, s.length });

        char[] ans = new char[s.length];
        int ansIndex = 0;
        int size = list.size();
        for (int i = 0; i < size; i++) {
            if (i != 0) {
                ans[ansIndex] = ' ';
                ansIndex++;
            }

            int[] item = list.get(i);
            for (int j = item[0]; j < item[1]; j++) {
                ans[ansIndex] = s[j];
                ansIndex++;
            }
        }

        for (int i = 0; i < s.length; i++) {
            s[i] = ans[i];
        }
    }
}
```
- Runtime: 1 ms (Beats: 99.84%)
- Memory: 48.18 MB (Beats: 96.07%)

<br>
