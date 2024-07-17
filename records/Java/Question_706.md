# [LeetCode Records](../../README.md) - Question 706 Design HashMap

### Attempt 1: Use LinkedList nested in ArrayList
```java
class MyHashMap {

    class Pair {
        int key;
        int value;

        Pair(int key, int value) {
            this.key = key;
            this.value = value;
        }
    }

    private List<List<Pair>> container;
    private int num = 400;

    public MyHashMap() {
        container = new ArrayList<>(num);
        for (int i = 0; i < num; i++) {
            container.add(new LinkedList<>());
        }
    }
    
    public void put(int key, int value) {
        List<Pair> list = container.get(key % num);
        for (Pair pair : list) {
            if (pair.key == key) {
                pair.value = value;
                return;
            }
        }

        list.add(new Pair(key, value));
    }
    
    public int get(int key) {
        List<Pair> list = container.get(key % num);
        for (Pair pair : list) {
            if (pair.key == key) {
                return pair.value;
            }
        }

        return -1;
    }
    
    public void remove(int key) {
        List<Pair> list = container.get(key % num);
        for (Pair pair : list) {
            if (pair.key == key) {
                list.remove(pair);
                return;
            }
        }
    }
}
```
- Runtime: 18 ms (Beats: 69.03%)
- Memory: 47.97 MB (Beats: 75.59%)

<br>
