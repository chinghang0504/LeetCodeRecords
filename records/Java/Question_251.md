# [LeetCode Records](../../README.md) - Question 251 Flatten 2D Vector

### Attempt 1: Convert int[][] to a List
```java
class Vector2D {

    private List<Integer> list;
    private Iterator<Integer> iterator;

    public Vector2D(int[][] vec) {
        list = new ArrayList<>();

        for (int[] arr : vec) {
            for (int num : arr) {
                list.add(num);
            }
        }

        iterator = list.iterator();
    }
    
    public int next() {
        return iterator.next();
    }
    
    public boolean hasNext() {
        return iterator.hasNext();
    }
}
```
- Runtime: 10 ms (Beats: 54.52%)
- Memory: 48.67 MB (Beats: 9.91%)

<br>
