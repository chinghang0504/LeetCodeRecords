# [LeetCode Records](../../README.md) - Question 3408 Design Task Manager

### Attempt 1: Use a TreeSet to store the sorted Task and a HashMap to store the task id and its Task key-value pairs
```java
class TaskManager {

    class Task {

        int priority;
        int taskId;
        int userId;

        Task(int priority, int taskId, int userId) {
            this.priority = priority;
            this.taskId = taskId;
            this.userId = userId;
        }

        int compareTo(Task task) {
            if (this.priority != task.priority) {
                return task.priority - this.priority;
            } else {
                return task.taskId - this.taskId;
            }
        }

        void update(int newPriority) {
            priority = newPriority;
        }
    }

    private SortedSet<Task> sortedSet;
    private Map<Integer, Task> taskIdToTaskMap;

    public TaskManager(List<List<Integer>> tasks) {
        sortedSet = new TreeSet<>((task1, task2) -> task1.compareTo(task2));
        taskIdToTaskMap = new HashMap<>();

        for (List<Integer> taskList : tasks) {
            int userId = taskList.get(0);
            int taskId = taskList.get(1);
            int priority = taskList.get(2);
            Task task = new Task(priority, taskId, userId);
            sortedSet.add(task);

            taskIdToTaskMap.put(taskId, task);
        }
    }
    
    public void add(int userId, int taskId, int priority) {
        Task task = new Task(priority, taskId, userId);
        sortedSet.add(task);

        taskIdToTaskMap.put(taskId, task);
    }
    
    public void edit(int taskId, int newPriority) {
        Task task = taskIdToTaskMap.get(taskId);
        sortedSet.remove(task);
        task.update(newPriority);
        sortedSet.add(task);
    }
    
    public void rmv(int taskId) {
        Task task = taskIdToTaskMap.get(taskId);
        sortedSet.remove(task);
        taskIdToTaskMap.remove(taskId);
    }
    
    public int execTop() {
        if (sortedSet.isEmpty()) {
            return -1;
        }

        Task task = sortedSet.removeFirst();
        taskIdToTaskMap.remove(task.taskId);
        return task.userId;
    }
}

/**
 * Your TaskManager object will be instantiated and called as such:
 * TaskManager obj = new TaskManager(tasks);
 * obj.add(userId,taskId,priority);
 * obj.edit(taskId,newPriority);
 * obj.rmv(taskId);
 * int param_4 = obj.execTop();
 */
```
- Runtime: 320 ms (Beats: 70.79%)
- Memory: 162.50 MB (Beats: 65.26%)

<br>
