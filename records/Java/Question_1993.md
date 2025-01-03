# [LeetCode Records](../../README.md) - Question 1993 Operations on Tree

### Attempt 1: Use a HashMap to store the parent and its children key-value pairs
```java
class LockingTree {

    private int[] parents;
    private int[] locks;
    private Map<Integer, List<Integer>> parentToChildrenMap;

    public LockingTree(int[] parent) {
        parents = parent;
        locks = new int[parent.length];
        
        parentToChildrenMap = new HashMap<>();
        for (int i = 0; i < parent.length; i++) {
            List<Integer> list = parentToChildrenMap.get(parent[i]);
            if (list == null) {
                list = new ArrayList<>();
                parentToChildrenMap.put(parent[i], list);
            }
            list.add(i);
        }
    }
    
    public boolean lock(int num, int user) {
        if (locks[num] != 0) {
            return false;
        } else {
            locks[num] = user;
            return true;
        }
    }
    
    public boolean unlock(int num, int user) {
        if (locks[num] != user) {
            return false;
        } else {
            locks[num] = 0;
            return true;
        }
    }
    
    public boolean upgrade(int num, int user) {
        if (locks[num] != 0) {
            return false;
        }

        int parent = parents[num];
        while (parent != -1) {
            if (locks[parent] != 0) {
                return false;
            }
            parent = parents[parent];
        }

        List<Integer> list = new ArrayList<>();
        addLockedDescendant(list, num);
        if (list.isEmpty()) {
            return false;
        }

        locks[num] = user;
        for (int child : list) {
            locks[child] = 0;
        }

        return true;
    }

    private void addLockedDescendant(List<Integer> list, int root) {
        if (locks[root] != 0) {
            list.add(root);
        }

        List<Integer> children = parentToChildrenMap.get(root);
        if (children != null) {
            for (int child : children) {
                addLockedDescendant(list, child);
            }
        }
    }
}

/**
 * Your LockingTree object will be instantiated and called as such:
 * LockingTree obj = new LockingTree(parent);
 * boolean param_1 = obj.lock(num,user);
 * boolean param_2 = obj.unlock(num,user);
 * boolean param_3 = obj.upgrade(num,user);
 */
```
- Runtime: 140 ms (Beats: 76.19%)
- Memory: 50.23 MB (Beats: 72.22%)

<br>
