# [LeetCode Records](../../README.md) - Question 1146 Snapshot Array

### Attempt 1: Use an ArrayList to store the changed value for each index
```java
class SnapshotArray {

    class Data {

        int snapId;
        int val;

        Data(int snapId, int val) {
            this.snapId = snapId;
            this.val = val;
        }
    }

    private List<List<Data>> container;
    private int snapId;

    public SnapshotArray(int length) {
        container = new ArrayList<>(length);
        for (int i = 0; i < length; i++) {
            List<Data> list = new ArrayList<>();
            list.add(new Data(snapId, 0));
            container.add(list);
        }
        snapId = 0;
    }
    
    public void set(int index, int val) {
        List<Data> list = container.get(index);
        list.add(new Data(snapId, val));
    }
    
    public int snap() {
        return snapId++;
    }
    
    public int get(int index, int snap_id) {
        List<Data> list = container.get(index);
        int val = 0;
        for (Data data : list) {
            if (data.snapId <= snap_id) {
                val = data.val;
            } else {
                break;
            }
        }
        return val;
    }
}

/**
 * Your SnapshotArray object will be instantiated and called as such:
 * SnapshotArray obj = new SnapshotArray(length);
 * obj.set(index,val);
 * int param_2 = obj.snap();
 * int param_3 = obj.get(index,snap_id);
 */
```
- Runtime: 2236 ms (Beats: 5.04%)
- Memory: 76.52 MB (Beats: 72.21%)

<br>
