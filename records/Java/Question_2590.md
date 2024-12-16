# [LeetCode Records](../../README.md) - Question 2590 Design a Todo List

### Attempt 1: Use a HashMap to store the user and its tasks key-value pairs
```java
class TodoList {

    class Task {

        int taskId;
        String description;
        int dueDate;
        Set<String> tags;

        Task(int taskId, String description, int dueDate, List<String> tags) {
            this.taskId = taskId;
            this.description = description;
            this.dueDate = dueDate;
            this.tags = new HashSet<>();
            
            for (String tag : tags) {
                this.tags.add(tag);
            }
        }

        int compareTo(Task task) {
            return this.dueDate - task.dueDate;
        }

        boolean contains(String tag) {
            return tags.contains(tag);
        }
    }

    private Map<Integer, SortedSet<Task>> userMap;
    private int currTaskId;

    public TodoList() {
        userMap = new HashMap<>();
        currTaskId = 1;
    }
    
    public int addTask(int userId, String taskDescription, int dueDate, List<String> tags) {
        SortedSet<Task> sortedSet = userMap.get(userId);
        if (sortedSet == null) {
            sortedSet = new TreeSet<>((t1, t2) -> t1.compareTo(t2));
            userMap.put(userId, sortedSet);
        }

        int taskId = currTaskId;
        sortedSet.add(new Task(taskId, taskDescription, dueDate, tags));
        currTaskId++;

        return taskId;
    }
    
    public List<String> getAllTasks(int userId) {
        List<String> ans = new ArrayList<>();
        SortedSet<Task> sortedSet = userMap.get(userId);
        if (sortedSet == null) {
            return ans;
        }

        for (Task task : sortedSet) {
            ans.add(task.description);
        }

        return ans;
    }
    
    public List<String> getTasksForTag(int userId, String tag) {
        List<String> ans = new ArrayList<>();
        SortedSet<Task> sortedSet = userMap.get(userId);
        if (sortedSet == null) {
            return ans;
        }

        for (Task task : sortedSet) {
            if (task.contains(tag)) {
                ans.add(task.description);
            }
        }

        return ans;
    }
    
    public void completeTask(int userId, int taskId) {
        SortedSet<Task> sortedSet = userMap.get(userId);
        if (sortedSet == null) {
            return;
        }

        Iterator<Task> iterator = sortedSet.iterator();
        while (iterator.hasNext()) {
            Task task = iterator.next();
            if (task.taskId == taskId) {
                iterator.remove();
                break;
            }
        }
    }
}

/**
 * Your TodoList object will be instantiated and called as such:
 * TodoList obj = new TodoList();
 * int param_1 = obj.addTask(userId,taskDescription,dueDate,tags);
 * List<String> param_2 = obj.getAllTasks(userId);
 * List<String> param_3 = obj.getTasksForTag(userId,tag);
 * obj.completeTask(userId,taskId);
 */
```
- Runtime: 57 ms (Beats: 76.77%)
- Memory: 46.79 MB (Beats: 61.62%)

<br>
