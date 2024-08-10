# [LeetCode Records](../../README.md) - Question 1065 Index Pairs of a String

### Attempt 1: Use an ArrayList to record the indices of substrings
```java
class Solution {
    public int[][] indexPairs(String text, String[] words) {
        List<int[]> list = new ArrayList<>();
        char[] arr = text.toCharArray();

        for (String word : words) {
            char[] target = word.toCharArray();

            for (int i = 0; i < arr.length - target.length + 1; i++) {
                if (isSubstring(arr, i, target)) {
                    list.add(new int[] { i, i + target.length - 1 });
                }
            }
        }

        int[][] answer = new int[list.size()][2];
        int size = 0;
        for (int[] item : list) {
            answer[size] = item;
            size++;
        }

        Arrays.sort(answer, (int[] o1, int[] o2) -> {
            if (o1[0] < o2[0]) {
                return -1;
            } else if (o1[0] > o2[0]) {
                return 1;
            }

            if (o1[1] < o2[1]) {
                return -1;
            } else if (o1[1] > o2[1]) {
                return 1;
            } else {
                return 0;
            }
        });

        return answer;
    }

    private boolean isSubstring(char[] arr, int start, char[] target) {
        for (int i = 0; i < target.length; i++) {
            if (arr[start + i] != target[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 86.67%)
- Memory: 43.46 MB (Beats: 97.33%)

<br>
