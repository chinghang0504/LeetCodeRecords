# [LeetCode Records](../../README.md) - Question 1436 Destination City

### Attempt 1: Use a HashSet to record the starting points
```java
class Solution {
    public String destCity(List<List<String>> paths) {
        Set<String> startingPoints = new HashSet<>();
        
        for (List<String> path : paths) {
            startingPoints.add(path.get(0));
        }

        for (List<String> path: paths) {
            String destination = path.get(1);
            if (!startingPoints.contains(destination)) {
                return destination;
            }
        }

        return null;
    }
}
```
- Runtime: 2 ms (Beats: 99.81%)
- Memory: 43.04 MB (Beats: 64.13%)

<br>
