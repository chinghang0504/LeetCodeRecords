# [LeetCode Records](../../README.md) - Question 2456 Most Popular Video Creator

### Attempt 1: Use two HashMap to store the data
```java
class Solution {

    class Item {

        String id;
        int view;

        Item(String id, int view) {
            this.id = id;
            this.view = view;
        }

        int compareTo(Item item) {
            if (this.view != item.view) {
                return item.view - this.view;
            } else {
                return this.id.compareTo(item.id);
            }
        }
    }

    public List<List<String>> mostPopularCreator(String[] creators, String[] ids, int[] views) {
        int n = creators.length;
        Map<String, Long> popularityMap = new HashMap<>();
        Map<String, SortedSet<Item>> viewMap = new HashMap<>(); 

        for (int i = 0; i < n; i++) {
            popularityMap.merge(creators[i], (long)views[i], Long::sum);

            SortedSet<Item> sortedSet = viewMap.get(creators[i]);
            if (sortedSet == null) {
                sortedSet = new TreeSet<>((item1, item2) -> item1.compareTo(item2));
                viewMap.put(creators[i], sortedSet);
            }
            sortedSet.add(new Item(ids[i], views[i]));
        }

        List<String> popularCreators = new ArrayList<>();
        long maxPopularity = 0;
        for (Map.Entry<String, Long> entry : popularityMap.entrySet()) {
            long popularity = entry.getValue();
            if (popularity > maxPopularity) {
                maxPopularity = popularity;
                popularCreators.clear();
                popularCreators.add(entry.getKey());
            } else if (popularity == maxPopularity) {
                popularCreators.add(entry.getKey());
            }
        }

        List<List<String>> ans = new ArrayList<>();
        for (String popularCreator : popularCreators) {
            SortedSet<Item> sortedSet = viewMap.get(popularCreator);
            ans.add(List.of(popularCreator, sortedSet.getFirst().id));
        }

        return ans;
    }
}
```
- Runtime: 68 ms (Beats: 27.85%)
- Memory: 105.22 MB (Beats: 20.45%)

<br>
