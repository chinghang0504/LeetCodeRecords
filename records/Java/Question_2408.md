# [LeetCode Records](../../README.md) - Question 2408 Design SQL

### Attempt 1: Use a HashMap to store the tables
```java
class SQL {

    Map<String, List<List<String>>> tables;

    public SQL(List<String> names, List<Integer> columns) {
        tables = new HashMap<>();
        int size = names.size();

        for (int i = 0; i < size; i++) {
            String tableName = names.get(i);
            List<List<String>> table = new ArrayList<>();
            tables.put(tableName, table);
        }
    }
    
    public void insertRow(String name, List<String> row) {
        List<List<String>> table = tables.get(name);
        table.add(row);
    }
    
    public void deleteRow(String name, int rowId) {
        List<List<String>> table = tables.get(name);
        table.set(rowId - 1, null);
    }
    
    public String selectCell(String name, int rowId, int columnId) {
        List<List<String>> table = tables.get(name);
        List<String> row = table.get(rowId - 1);
        return row.get(columnId - 1);
    }
}

/**
 * Your SQL object will be instantiated and called as such:
 * SQL obj = new SQL(names, columns);
 * obj.insertRow(name,row);
 * obj.deleteRow(name,rowId);
 * String param_3 = obj.selectCell(name,rowId,columnId);
 */
```
- Runtime: 100 ms (Beats: 81.53%)
- Memory: 62.28 MB (Beats: 56.76%)

<br>
