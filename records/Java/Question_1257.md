# [LeetCode Records](../../README.md) - Question 1257 Smallest Common Region

### Attempt 1: Use a HashMap to store the small region and large region key-value pairs
```java
class Solution {

    private Map<String, String> smallToLargeRegionMap;

    public String findSmallestRegion(List<List<String>> regions, String region1, String region2) {
        smallToLargeRegionMap = new HashMap<>();

        for (List<String> region : regions) {
            int regionSize = region.size();
            String largeRegion = region.get(0);
            for (int i = 1; i < regionSize; i++) {
                smallToLargeRegionMap.put(region.get(i), largeRegion);
            }
        }

        Set<String> set = new HashSet<>();
        String largeRegion = region1;
        while (largeRegion != null) {
            set.add(largeRegion);
            largeRegion = smallToLargeRegionMap.get(largeRegion);
        }

        largeRegion = region2;
        while (!set.contains(largeRegion)) {
            largeRegion = smallToLargeRegionMap.get(largeRegion);
        }

        return largeRegion;
    }
}
```
- Runtime: 9 ms (Beats: 98.95%)
- Memory: 46.55 MB (Beats: 93.33%)

<br>
