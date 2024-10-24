# [LeetCode Records](../../README.md) - Question 245 Shortest Word Distance III

### Attempt 1: Use a HashMap to store the word and its indices key-value pairs
```java
class Solution {
    public int shortestWordDistance(String[] wordsDict, String word1, String word2) {
        Map<String, List<Integer>> map = new HashMap<>();

        for (int i = 0; i < wordsDict.length; i++) {
            List<Integer> list = map.get(wordsDict[i]);
            if (list == null) {
                list = new ArrayList<>();
                map.put(wordsDict[i], list);
            }

            list.add(i);
        }

        if (word1.equals(word2)) {
            List<Integer> list = map.get(word1);
            int size = list.size();
            int minDiff = Integer.MAX_VALUE;

            int prevVal = list.get(0);
            for (int i = 1; i < size; i++) {
                int nextVal = list.get(i);
                minDiff = Math.min(minDiff, nextVal - prevVal);
                prevVal = nextVal;
            }

            return minDiff;
        } else {
            List<Integer> list1 = map.get(word1);
            List<Integer> list2 = map.get(word2);
            int size1 = list1.size();
            int size2 = list2.size();
            int minDiff = Integer.MAX_VALUE;

            int index1 = 0;
            int index2 = 0;
            while (index1 < size1 && index2 < size2) {
                int val1 = list1.get(index1);
                int val2 = list2.get(index2);
                minDiff = Math.min(minDiff, Math.abs(val1 - val2));

                if (val1 <= val2) {
                    index1++;
                } else {
                    index2++;
                }
            }

            return minDiff;
        }
    }
}
```
- Runtime: 40 ms (Beats: 18.90%)
- Memory: 57.63 MB (Beats: 96.06%)

<br>
