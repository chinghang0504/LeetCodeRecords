# [LeetCode Records](../../README.md) - Question 359 Logger Rate Limiter

### Attempt 1: Use a HashMap
```java
class Logger {

    private final Map<String, Integer> map;

    public Logger() {
        map = new HashMap<>();
    }

    public boolean shouldPrintMessage(int timestamp, String message) {
        Integer prevTimestamp = map.get(message);
        if (prevTimestamp != null && timestamp < prevTimestamp + 10) {
            return false;
        }
        
        map.put(message, timestamp);
        return true;
    }
}

```
- Runtime: 29 ms (Beats: 99.52%)
- Memory: 55.54 MB (Beats: 13.56%)

<br>
