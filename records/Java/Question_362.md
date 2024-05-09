# [LeetCode Records](../../README.md) - Question 362 Design Hit Counter

### Attempt 1: Use a LinkedList to record the hits
```java
class HitCounter {

    private Queue<Integer> queue;

    public HitCounter() {
        queue = new LinkedList<>();
    }

    public void hit(int timestamp) {
        queue.add(timestamp);
    }

    public int getHits(int timestamp) {
        int min = timestamp - 300;

        Integer item = queue.peek();
        while (item != null) {
            if (item <= min) {
                queue.remove();
            } else {
                break;
            }

            item = queue.peek();
        }

        return queue.size();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.18 MB (Beats: 83.87%)

<br>
