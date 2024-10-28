# [LeetCode Records](../../README.md) - Question 356 Line Reflection

### Attempt 1: Use a HashMap to group the x values of the same y value
```java
class Solution {
    public boolean isReflected(int[][] points) {
        Map<Integer, Set<Double>> map = new HashMap<>();

        for (int[] point : points) {
            Set<Double> set = map.get(point[1]);
            if (set == null) {
                set = new HashSet<>();
                map.put(point[1], set);
            }
            set.add((double) point[0]);
        }

        double center = Double.MIN_VALUE;
        for (Set<Double> set : map.values()) {
            for (double x : set) {
                if (center == Double.MIN_VALUE) {
                    int size = set.size();
                    if (size == 1) {
                        center = x;
                    } else {
                        Double[] arr = set.toArray(Double[]::new);
                        Arrays.sort(arr);
                        center = (arr[0] + arr[size - 1]) / 2.0;
                    }
                } else {
                    double target = center - x + center;
                    if (!set.contains(target)) {
                        return false;
                    }
                }
            }
        }

        return true;
    }
}
```
- Runtime: 8 ms (Beats: 91.67%)
- Memory: 47.40 MB (Beats: 81.03%)

<br>
