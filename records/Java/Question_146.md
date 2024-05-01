# [LeetCode Records](../../README.md) - Question 146 LRU Cache

### Attempt 1: Use a HashMap and a LinkedList
```java
class LRUCache {

    private int capacity;
    private Map<Integer, Integer> map;
    private List<Integer> list;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        this.map = new HashMap<>(capacity);
        this.list = new LinkedList<>();
    }

    public int get(int key) {
        // Get the value from the map
        Integer value = this.map.get(key);

        // The key does not exist
        if (value == null) {
            return -1;
        }

        // The key exists
        // Remove the key in the list and add it back to the end
        list.remove((Integer) key);
        list.addLast(key);

        return value;
    }

    public void put(int key, int value) {
        // The key is already exists
        if (this.map.containsKey(key)) {
            // Update the map
            this.map.put(key, value);

            // Remove the key in the list and add it back to the end
            list.remove((Integer) key);
            list.addLast(key);

            return;
        }

        // The key does not exist
        // The capacity is not enough
        if (this.map.size() == this.capacity) {
            Integer victimKey = this.list.removeFirst();
            this.map.remove(victimKey);
        }

        this.map.put(key, value);
        this.list.addLast(key);
    }
}
```
- Runtime: 999 ms (Beats: 5.02%)
- Memory: 123.04 MB (Beats: 25.47%)

<br>
