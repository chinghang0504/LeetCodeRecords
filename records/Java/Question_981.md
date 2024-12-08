# [LeetCode Records](../../README.md) - Question 981 Time Based Key-Value Store

### Attempt 1: Use a HashMap to store the key and the sorted set of items key-value pairs
```java
class TimeMap {

    class Item {
        String value;
        int timestamp;

        Item(String value, int timestamp) {
            this.value = value;
            this.timestamp = timestamp;
        }

        @Override
        public boolean equals(Object obj) {
            return this.timestamp == ((Item)obj).timestamp;
        }
    }

    private Map<String, SortedSet<Item>> map;

    public TimeMap() {
        map = new HashMap<>();
    }
    
    public void set(String key, String value, int timestamp) {
        SortedSet<Item> set = map.get(key);
        if (set == null) {
            set = new TreeSet<>((item1, item2) -> {
                return item2.timestamp - item1.timestamp;
            });
            map.put(key, set);
        }

        set.add(new Item(value, timestamp));
    }
    
    public String get(String key, int timestamp) {
        SortedSet<Item> set = map.get(key);
        if (set == null) {
            return "";
        }

        for (Item item : set) {
            if (timestamp >= item.timestamp) {
                return item.value;
            }
        }

        return "";
    }
}

/**
 * Your TimeMap object will be instantiated and called as such:
 * TimeMap obj = new TimeMap();
 * obj.set(key,value,timestamp);
 * String param_2 = obj.get(key,timestamp);
 */
```
- Runtime: 139 ms (Beats: 67.76%)
- Memory: 123.11 MB (Beats: 8.32%)

<br>
