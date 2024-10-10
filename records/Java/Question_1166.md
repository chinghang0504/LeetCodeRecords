# [LeetCode Records](../../README.md) - Question 1166 Design File System

### Attempt 1: Use splits() to get the parent folders and check every parent folder
```java
class FileSystem {

    private Map<String, Integer> map;

    public FileSystem() {
        map = new HashMap<>();
    }
    
    public boolean createPath(String path, int value) {
        String[] splits = path.split("/");
        
        String currPath = "";
        for (int i = 1; i < splits.length - 1; i++) {
            currPath += "/" + splits[i];
            if (!map.containsKey(currPath)) {
                return false;
            }
        }

        currPath += "/" + splits[splits.length - 1];
        if (map.containsKey(currPath)) {
            return false;
        } else {
            map.put(currPath, value);
            return true;
        }
    }
    
    public int get(String path) {
        Integer value = map.get(path);
        return value == null ? -1 : value;
    }
}

/**
 * Your FileSystem object will be instantiated and called as such:
 * FileSystem obj = new FileSystem();
 * boolean param_1 = obj.createPath(path,value);
 * int param_2 = obj.get(path);
 */
```
- Runtime: 97 ms (Beats: 60.72%)
- Memory: 55.58 MB (Beats: 67.24%)

<br>

### Attempt 2: Use lastIndexOf() and substring() to get the parent folder and check only once
```java
class FileSystem {

    private Map<String, Integer> map;

    public FileSystem() {
        map = new HashMap<>();
    }
    
    public boolean createPath(String path, int value) {
        if (map.containsKey(path)) {
            return false;
        }

        int lastIndex = path.lastIndexOf("/");
        String parentPath = path.substring(0, lastIndex);
        if (!parentPath.isEmpty() && !map.containsKey(parentPath)) {
            return false;
        }

        map.put(path, value);
        return true;
    }
    
    public int get(String path) {
        Integer value = map.get(path);
        return value == null ? -1 : value;
    }
}

/**
 * Your FileSystem object will be instantiated and called as such:
 * FileSystem obj = new FileSystem();
 * boolean param_1 = obj.createPath(path,value);
 * int param_2 = obj.get(path);
 */
```
- Runtime: 79 ms (Beats: 93.21%)
- Memory: 54.46 MB (Beats: 100.00%)

<br>
