# [LeetCode Records](../../README.md) - Question 893 Groups of Special-Equivalent Strings

### Attempt 1: Find the odd index character counts and the even index character counts
```java
class Solution {
    public int numSpecialEquivGroups(String[] words) {
        int[][][] wordCounts = new int[words.length][][];
        for (int i = 0; i < words.length; i++) {
            wordCounts[i] = getCounts(words[i]);
        }

        List<int[][]> list = new ArrayList<>();
        for (int[][] wordCount : wordCounts) {
            boolean noEqual = true;
            for (int[][] item : list) {
                if (isEqualCounts(wordCount, item)) {
                    noEqual = false;
                    break;
                }
            }

            if (noEqual) {
                list.add(wordCount);
            }
        }

        return list.size();
    }

    private boolean isEqualCounts(int[][] counts1, int[][] counts2) {
        return Arrays.equals(counts1[0], counts2[0]) && Arrays.equals(counts1[1], counts2[1]);
    }

    private int[][] getCounts(String word) {
        char[] arr = word.toCharArray();
        int[] oddCounts = new int[26];
        int[] evenCounts = new int[26];

        for (int i = 0; i < arr.length; i++) {
            if (i % 2 == 1) {
                oddCounts[arr[i] - 'a']++;
            } else {
                evenCounts[arr[i] - 'a']++;
            }
        }

        return new int[][]{ oddCounts, evenCounts };
    }
}
```
- Runtime: 22 ms (Beats: 14.34%)
- Memory: 44.26 MB (Beats: 58.06%)

<br>
