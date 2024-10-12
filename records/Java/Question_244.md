# [LeetCode Records](../../README.md) - Question 244 Shortest Word Distance II

### Attempt 1: Use a HashMap to store the word and its index key-value pairs
```java
class WordDistance {

    private Map<String, List<Integer>> map;

    public WordDistance(String[] wordsDict) {
        map = new HashMap<>();
        for (int i = 0; i < wordsDict.length; i++) {
            List<Integer> list = map.get(wordsDict[i]);
            if (list == null) {
                list = new ArrayList<>();
                map.put(wordsDict[i], list);
            }
            list.add(i);
        }
    }
    
    public int shortest(String word1, String word2) {
        List<Integer> list1 = map.get(word1);
        List<Integer> list2 = map.get(word2);

        int minDistance = Integer.MAX_VALUE;
        for (int i : list1) {
            for (int j : list2) {
                minDistance = Math.min(minDistance, Math.abs(i - j));
            }
        }

        return minDistance;
    }
}

/**
 * Your WordDistance object will be instantiated and called as such:
 * WordDistance obj = new WordDistance(wordsDict);
 * int param_1 = obj.shortest(word1,word2);
 */
```
- Runtime: 29 ms (Beats: 66.48%)
- Memory: 51.33 MB (Beats: 41.34%)

<br>
