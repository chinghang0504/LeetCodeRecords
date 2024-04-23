# [LeetCode Records](../README.md) - Question 170 Two Sum III - Data structure design

### Attempt 1: Use a HashMap
```java
class TwoSum {

    private final Map<Integer, Integer> map;

    public TwoSum() {
        map = new HashMap<>();
    }

    public void add(int number) {
        map.merge(number, 1, Integer::sum);
    }

    public boolean find(int value) {
        for (int key : map.keySet()) {
            int target = value - key;
            if (key != target) {
                if (map.containsKey(target)) {
                    return true;
                }
            } else if (map.get(key) > 1) {
                return true;
            }
        }

        return false;
    }
}
```
- Runtime: 80 ms (Beats: 74.87%)
- Memory: 52.49 MB (Beats: 52.34%)

<br>
