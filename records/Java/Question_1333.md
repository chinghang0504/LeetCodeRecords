# [LeetCode Records](../../README.md) - Question 1333 Filter Restaurants by Vegan-Friendly, Price and Distance

### Attempt 1: Filter and store the restaurants in the ArrayList
```java
class Solution {
    public List<Integer> filterRestaurants(int[][] restaurants, int veganFriendly, int maxPrice, int maxDistance) {
        List<int[]> list = new ArrayList<>();

        for (int[] restaurant : restaurants) {
            if (veganFriendly == 1 && restaurant[2] != 1) {
                continue;
            }

            if (restaurant[3] <= maxPrice && restaurant[4] <= maxDistance) {
                list.add(restaurant);
            }
        }

        list.sort((r1, r2) -> r1[1] != r2[1] ? r2[1] - r1[1] : r2[0] - r1[0]);

        return list.stream().map(r -> r[0]).toList();
    }
}
```
- Runtime: 7 ms (Beats: 53.44%)
- Memory: 52.96 MB (Beats: 31.30%)

<br>
