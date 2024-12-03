# [LeetCode Records](../../README.md) - Question 2502 Design Memory Allocator

### Attempt 1: Check every space in the memory
```java
class Allocator {

    private boolean[] memory;
    private Map<Integer, List<int[]>> idToMemory;

    public Allocator(int n) {
        memory = new boolean[n];
        idToMemory = new HashMap<>();
    }
    
    public int allocate(int size, int mID) {
        for (int i = 0; i < memory.length - size + 1; i++) {
            if (!memory[i]) {
                boolean isEmpty = true;

                for (int j = 1; j < size; j++) {
                    if (memory[i + j]) {
                        isEmpty = false;
                        break;
                    }
                }

                if (isEmpty) {
                    for (int j = 0; j < size; j++) {
                        memory[i + j] = true;
                    }

                    List<int[]> list = idToMemory.get(mID);
                    if (list == null) {
                        list = new ArrayList<>();
                        idToMemory.put(mID, list);
                    }
                    list.add(new int[]{ i, i + size });

                    return i;
                }
            }
        }

        return -1;
    }
    
    public int freeMemory(int mID) {
        List<int[]> list = idToMemory.get(mID);
        if (list == null) {
            return 0;
        }

        int total = 0;
        for (int[] item : list) {
            total += item[1] - item[0];

            for (int i = item[0]; i < item[1]; i++) {
                memory[i] = false;
            }
        }
        list.clear();

        return total;
    }
}

/**
 * Your Allocator object will be instantiated and called as such:
 * Allocator obj = new Allocator(n);
 * int param_1 = obj.allocate(size,mID);
 * int param_2 = obj.freeMemory(mID);
 */
```
- Runtime: 1335 ms (Beats: 5.10%)
- Memory: 45.78 MB (Beats: 16.55%)

<br>
