# [LeetCode Records](../../README.md) - Question 690 Employee Importance

### Attempt 1: Use a HashMap to store id and employee key-value pairs
```java
/*
// Definition for Employee.
class Employee {
    public int id;
    public int importance;
    public List<Integer> subordinates;
};
*/

class Solution {
    public int getImportance(List<Employee> employees, int id) {
        Map<Integer, Employee> map = new HashMap<>();
        for (Employee employee : employees) {
            map.put(employee.id, employee);
        }

        Employee target = map.get(id);
        return getImportanceRecursion(map, target);
    }

    private int getImportanceRecursion(Map<Integer, Employee> map, Employee root) {
        int sum = root.importance;

        for (int id : root.subordinates) {
            sum += getImportanceRecursion(map, map.get(id));
        }

        return sum;
    }
}
```
- Runtime: 4 ms (Beats: 99.37%)
- Memory: 46.28 MB (Beats: 44.99%)

<br>
