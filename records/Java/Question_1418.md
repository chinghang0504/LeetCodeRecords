# [LeetCode Records](../../README.md) - Question 1418 Display Table of Food Orders in a Restaurant

### Attempt 1: Use a nested HashMap to store the orders
```java
class Solution {
    public List<List<String>> displayTable(List<List<String>> orders) {
        Set<String> foodNames = new HashSet<>();
        Set<String> tableNumbers = new HashSet<>();
        Map<String, Map<String, Integer>> map = new HashMap<>();
        for (List<String> order : orders) {
            String tableNumber = order.get(1);
            String foodName = order.get(2);
            foodNames.add(foodName);
            tableNumbers.add(tableNumber);

            Map<String, Integer> foodMap = map.get(foodName);
            if (foodMap == null) {
                foodMap = new HashMap<>();
                map.put(foodName, foodMap);
            }
            foodMap.merge(tableNumber, 1, Integer::sum);
        }

        List<List<String>> ans = new ArrayList<>();
        List<String> foodNameList = new ArrayList<>(foodNames);
        foodNameList.sort(null);
        List<String> tableNumberList = new ArrayList<>(tableNumbers);
        tableNumberList.sort((s1, s2) -> {
            return Integer.valueOf(s1) - Integer.valueOf(s2);
        });

        ans.add(foodNameList);
        for (String tableNumber : tableNumberList) {
            List<String> row = new ArrayList<>();
            row.add(tableNumber);

            for (String foodName : foodNameList) {
                Map<String, Integer> foodMap = map.get(foodName);
                Integer count = foodMap.get(tableNumber);
                if (count == null) {
                    row.add("0");
                } else {
                    row.add(String.valueOf(count));
                }
            }

            ans.add(row);
        }
        foodNameList.addFirst("Table");

        return ans;
    }
}
```
- Runtime: 31 ms (Beats: 80.95%)
- Memory: 51.86 MB (Beats: 94.49%)

<br>
