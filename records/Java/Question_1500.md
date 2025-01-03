# [LeetCode Records](../../README.md) - Question 1500 Design a File Sharing System

### Attempt 1: Use a SortedSet in each chunk to store the owned IDs
```java
class FileSharing {

    private List<SortedSet<Integer>> chunks;
    private int currId;
    private PriorityQueue<Integer> unusedIds;
    private Map<Integer, List<Integer>> idToChunks;

    public FileSharing(int m) {
        chunks = new ArrayList<>(m);
        for (int i = 0; i < m; i++) {
            chunks.add(new TreeSet<>());
        }

        currId = 1;
        unusedIds = new PriorityQueue<>();
        idToChunks = new HashMap<>();
    }
    
    public int join(List<Integer> ownedChunks) {
        int id = currId;
        if (!unusedIds.isEmpty()) {
            id = unusedIds.poll();
        } else {
            currId++;
        }

        for (int chunk : ownedChunks) {
            chunks.get(chunk - 1).add(id);
        }

        idToChunks.put(id, ownedChunks);

        return id;
    }
    
    public void leave(int userID) {
        for (int chunkId : idToChunks.get(userID)) {
            chunks.get(chunkId - 1).remove(userID);
        }
        unusedIds.add(userID);
    }
    
    public List<Integer> request(int userID, int chunkID) {
        SortedSet<Integer> sortedSet = chunks.get(chunkID - 1);
        if (sortedSet.isEmpty()) {
            return List.of();
        } else {
            List<Integer> ids = sortedSet.stream().toList();
            sortedSet.add(userID);
            idToChunks.get(userID).add(chunkID);
            return ids;
        }
    }
}

/**
 * Your FileSharing object will be instantiated and called as such:
 * FileSharing obj = new FileSharing(m);
 * int param_1 = obj.join(ownedChunks);
 * obj.leave(userID);
 * List<Integer> param_3 = obj.request(userID,chunkID);
 */
```
- Runtime: 128 ms (Beats: 79.49%)
- Memory: 65.38 MB (Beats: 12.82%)

<br>
