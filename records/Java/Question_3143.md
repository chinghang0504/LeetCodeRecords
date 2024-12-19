# [LeetCode Records](../../README.md) - Question 3143 Maximum Points Inside the Square

### Attempt 1: Use a HashMap to store the distance and its characters key-value pairs
```java
class Solution {
    public int maxPointsInsideSquare(int[][] points, String s) {
        char[] arr = s.toCharArray();
        Map<Integer, List<Character>> distanceMap = new HashMap<>();
        for (int i = 0; i < points.length; i++) {
            int distance = getDistance(points[i]);
            List<Character> list = distanceMap.get(distance);
            if (list == null) {
                list = new ArrayList<>();
                distanceMap.put(distance, list);
            }
            list.add(arr[i]);
        }

        List<Map.Entry<Integer, List<Character>>> entryList = new ArrayList(distanceMap.entrySet());
        entryList.sort((e1, e2) -> e1.getKey() - e2.getKey());

        Set<Character> set = new HashSet<>();
        for (Map.Entry<Integer, List<Character>> entry : entryList) {
            int currSize = set.size();

            for (char ch : entry.getValue()) {
                if (set.contains(ch)) {
                    return currSize;
                } else {
                    set.add(ch);
                }
            }
        }

        return set.size();
    }

    private int getDistance(int[] point) {
        return Math.max(Math.abs(point[0]), Math.abs(point[1]));
    }
}
```
- Runtime: 39 ms (Beats: 43.48%)
- Memory: 77.13 MB (Beats: 85.51%)

<br>
