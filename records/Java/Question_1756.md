# [LeetCode Records](../../README.md) - Question 1756 Design Most Recently Used Queue

### Attempt 1: Use a LinkedList as a container
```java
class MRUQueue {

    private List<Integer> list;

    public MRUQueue(int n) {
        list = new LinkedList<>();

        for (int i = 1; i <= n; i++) {
            list.add(i);
        }
    }
    
    public int fetch(int k) {
        int val = list.remove(k - 1);
        list.add(val);
        return val;
    }
}

/**
 * Your MRUQueue object will be instantiated and called as such:
 * MRUQueue obj = new MRUQueue(n);
 * int param_1 = obj.fetch(k);
 */
```
- Runtime: 34 ms (Beats: 40.38%)
- Memory: 45.64 MB (Beats: 66.35%)

<br>
