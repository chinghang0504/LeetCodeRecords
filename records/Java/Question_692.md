# [LeetCode Records](../../README.md) - Question 692 Top K Frequent Words

### Attempt 1: Use a HashMap to store the word and its count key-value pairs
```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        Map<String, Integer> map = new HashMap<>();
        for (String word : words) {
            map.merge(word, 1, Integer::sum);
        }

        List<Map.Entry<String, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort((e1, e2) -> {
            int val1 = e1.getValue();
            int val2 = e2.getValue();
            if (val1 != val2) {
                return val2 - val1;
            } else {
                return e1.getKey().compareTo(e2.getKey());
            }
        });

        List<String> ans = new ArrayList<>();
        for (int i = 0; i < k; i++) {
            ans.add(list.get(i).getKey());
        }

        return ans;
    }
}
```
- Runtime: 6 ms (Beats: 98.02%)
- Memory: 44.79 MB (Beats: 43.30%)

<br>
