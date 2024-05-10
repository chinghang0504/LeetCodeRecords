# [LeetCode Records](../../README.md) - Question 341 Flatten Nested List Iterator

### Attempt 1: Get the flatten list first
```java
public class NestedIterator implements Iterator<Integer> {

    private List<Integer> list;
    private Iterator<Integer> iterator;

    public NestedIterator(List<NestedInteger> nestedList) {
        list = new ArrayList<>();

        getAllIntegers(nestedList);

        iterator = list.iterator();
    }

    private void getAllIntegers(List<NestedInteger> nestedList) {
        for (NestedInteger item : nestedList) {
            if (item.isInteger()) {
                list.add(item.getInteger());
            } else {
                getAllIntegers(item.getList());
            }
        }
    }

    @Override
    public Integer next() {
        return iterator.next();
    }

    @Override
    public boolean hasNext() {
        return iterator.hasNext();
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 46.03 MB (Beats: 15.39%)

<br>
