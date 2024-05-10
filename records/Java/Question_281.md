# [LeetCode Records](../../README.md) - Question 281 Zigzag Iterator

### Attempt 1: Combine to two Lists into a List
```java
public class ZigzagIterator {

    private List<Integer> v;
    private Iterator<Integer> iterator;

    public ZigzagIterator(List<Integer> v1, List<Integer> v2) {
        v = new ArrayList<>();
        Iterator<Integer> iterator1 = v1.iterator();
        Iterator<Integer> iterator2 = v2.iterator();
        
        while (iterator1.hasNext() && iterator2.hasNext()) {
            v.add(iterator1.next());
            v.add(iterator2.next());
        }
        while (iterator1.hasNext()) {
            v.add(iterator1.next());
        }
        while (iterator2.hasNext()) {
            v.add(iterator2.next());
        }

        iterator = v.iterator();
    }

    public int next() {
        return iterator.next();
    }

    public boolean hasNext() {
        return iterator.hasNext();
    }
}
```
- Runtime: 2 ms (Beats: 42.97%)
- Memory: 44.56 MB (Beats: 67.64%)

<br>
