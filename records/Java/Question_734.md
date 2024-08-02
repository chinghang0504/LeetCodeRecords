# [LeetCode Records](../../README.md) - Question 734 Sentence Similarity

### Attempt 1: Use a HashMap to save the pairs
```java
class Solution {
    public boolean areSentencesSimilar(String[] sentence1, String[] sentence2, List<List<String>> similarPairs) {
        if (sentence1.length != sentence2.length) {
            return false;
        }

        Map<String, Set<String>> map = new HashMap<>();
        for (List<String> pair : similarPairs) {
            String str1 = pair.get(0);
            String str2 = pair.get(1);

            Set<String> set1 = map.get(str1);
            if (set1 == null) {
                set1 = new HashSet<>();
                map.put(str1, set1);
            }
            set1.add(str2);

            Set<String> set2 = map.get(str2);
            if (set2 == null) {
                set2 = new HashSet<>();
                map.put(str2, set2);
            }
            set2.add(str1);
        }

        for (int i = 0; i < sentence1.length; i++) {
            if (!sentence1[i].equals(sentence2[i])) {
                Set<String> set = map.get(sentence1[i]);
                if (set == null) {
                    return false;
                } else if (!set.contains(sentence2[i])) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 98.30%)
- Memory: 42.87 MB (Beats: 25.00%)

<br>
