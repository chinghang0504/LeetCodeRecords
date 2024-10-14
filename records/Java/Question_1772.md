# [LeetCode Records](../../README.md) - Question 1772 Sort Features by Popularity

### Attempt 1: Use a HashMap to store the feature and its count key-value pairs
```java
class Solution {
    public String[] sortFeatures(String[] features, String[] responses) {
        Map<String, Integer> featureIndexMap = new HashMap<>();
        Map<String, Integer> featureCountMap = new HashMap<>();
        for (int i = 0; i < features.length; i++) {
            featureIndexMap.put(features[i], i);
            featureCountMap.put(features[i], 0);
        }

        for (String response : responses) {
            Set<String> responseWordSet = new HashSet<>();
            for (String word : response.split("\s")) {
                Integer count = featureCountMap.get(word);
                if (count != null && !responseWordSet.contains(word)) {
                    responseWordSet.add(word);
                    featureCountMap.put(word, count + 1);
                }
            }
        }

        Arrays.sort(features, (f1, f2) -> {
            int count1 = featureCountMap.get(f1);
            int count2 = featureCountMap.get(f2);
            return count1 != count2 ? count2 - count1 : featureIndexMap.get(f1) - featureIndexMap.get(f2);
        });

        return features;
    }
}
```
- Runtime: 60 ms (Beats: 50.00%)
- Memory: 47.47 MB (Beats: 73.91%)

<br>
