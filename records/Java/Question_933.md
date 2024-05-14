# [LeetCode Records](../../README.md) - Question 933 Number of Recent Calls

### Attempt 1: Use a LinkedList
```java
class RecentCounter {

    private List<Integer> list;

    public RecentCounter() {
        list = new LinkedList<>();
    }

    public int ping(int t) {
        list.add(t);
        int min = t - 3000;
        Iterator<Integer> it = list.iterator();
        while (it.hasNext()) {
            if (it.next() < min) {
                it.remove();
            } else {
                break;
            }
        }
        return list.size();
    }
}
```
- Runtime: 22 ms (Beats: 42.86%)
- Memory: 51.20 MB (Beats: 94.46%)

<br>
