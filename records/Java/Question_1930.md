# [LeetCode Records](../../README.md) - Question 1930 Unique Length-3 Palindromic Subsequences

### Attempt 1: Use a HashMap to store the character and its indices key-value pairs
```java
class Solution {
    public int countPalindromicSubsequence(String s) {
        char[] arr = s.toCharArray();
        Map<Character, List<Integer>> map = new HashMap<>();
        for (int i = 0; i < arr.length; i++) {
            List<Integer> list = map.get(arr[i]);
            if (list == null) {
                list = new ArrayList<>();
                map.put(arr[i], list);
            }

            list.add(i);
        }

        int count = 0;
        for (List<Integer> list : map.values()) {
            int firstIndex = list.getFirst();
            int lastIndex = list.getLast();
            boolean[] checked = new boolean[26];
            for (int i = firstIndex + 1; i < lastIndex; i++) {
                if (!checked[arr[i] - 'a']) {
                    checked[arr[i] - 'a'] = true;
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 34 ms (Beats: 90.31%)
- Memory: 49.94 MB (Beats: 5.76%)

<br>

### Attempt 2: Use an int[][] to store the character and its first and last indices
```java
class Solution {
    public int countPalindromicSubsequence(String s) {
        char[] arr = s.toCharArray();
        int[][] charIndices = new int[26][2];
        for (int i = 0; i < arr.length; i++) {
            int index = charIndices[arr[i] - 'a'][0] == 0 ? 0 : 1;
            charIndices[arr[i] - 'a'][index] = i + 1;
        }

        int count = 0;
        for (int i = 0; i < 26; i++) {
            int firstIndex = charIndices[i][0];
            int lastIndex = charIndices[i][1];
            if (lastIndex - firstIndex > 1) {
                boolean[] checked = new boolean[26];
                for (int j = firstIndex; j < lastIndex - 1; j++) {
                    if (!checked[arr[j] - 'a']) {
                        checked[arr[j] - 'a'] = true;
                        count++;
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 17 ms (Beats: 95.03%)
- Memory: 45.17 MB (Beats: 89.79%)

<br>
