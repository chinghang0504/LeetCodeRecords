# [LeetCode Records](../../README.md) - Question 705 Design HashSet

### Attempt 1: Use LinkedList nested in ArrayList
```java
class MyHashSet {

    List<List<Integer>> container;

    public MyHashSet() {
        container = new ArrayList<>();
        for (int i = 0; i < 10; i++) {
            container.add(new LinkedList<>());
        }
    }
    
    public void add(int key) {
        List<Integer> list = container.get(key % 10);
        if (!list.contains((Integer)key)) {
            list.add(key);
        }
    }
    
    public void remove(int key) {
        List<Integer> list = container.get(key % 10);
        list.remove((Integer)key);
    }
    
    public boolean contains(int key) {
        List<Integer> list = container.get(key % 10);
        return list.contains((Integer)key);
    }
}
```
- Runtime: 76 ms (Beats: 17.31%)
- Memory: 54.58 MB (Beats: 21.50%)

<br>
