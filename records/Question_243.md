# [LeetCode Records](../README.md) - Question 243 Shortest Word Distance

### Attempt 1: Get all the index of strings first
```java
class Solution {
    public int shortestDistance(String[] wordsDict, String word1, String word2) {
        List<Integer> list1 = new ArrayList<>();
        List<Integer> list2 = new ArrayList<>();

        for (int i = 0; i < wordsDict.length; i++) {
            if (wordsDict[i].equals(word1)) {
                list1.add(i);
            } else if (wordsDict[i].equals(word2)) {
                list2.add(i);
            }
        }

        int size1 = list1.size();
        int size2 = list2.size();
        int min = Integer.MAX_VALUE;
        for (int i = 0; i < size1; i++) {
            int index1 = list1.get(i);
            for (int j = 0; j < size2; j++) {
                int index2 = list2.get(j);
                min = Math.min(min, Math.abs(index1 - index2));
            }
        }

        return min;
    }
}
```
- Runtime: 2 ms (Beats: 92.92%)
- Memory: 45.77 MB (Beats: 65.46%)

<br>
