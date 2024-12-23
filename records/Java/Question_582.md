# [LeetCode Records](../../README.md) - Question 582 Kill Process

### Attempt 1: Use a HashMap to store the parent and its childs key-value paris
```java
class Solution {
    public List<Integer> killProcess(List<Integer> pid, List<Integer> ppid, int kill) {
        Map<Integer, List<Integer>> parentMap = new HashMap<>();
        int size = pid.size();
        for (int i = 0; i < size; i++) {
            int parent = ppid.get(i);
            int child = pid.get(i);
            List<Integer> childs = parentMap.get(parent);
            if (childs == null) {
                childs = new ArrayList<>();
                parentMap.put(parent, childs);
            }
            childs.add(child);
        }

        List<Integer> ans = new ArrayList<>();
        addChildProcesses(parentMap, ans, kill);

        return ans;
    }

    private void addChildProcesses(Map<Integer, List<Integer>> parentMap, List<Integer> ans, int parent) {
        ans.add(parent);

        List<Integer> childs = parentMap.get(parent);
        if (childs == null) {
            return;
        }

        for (int child : childs) {
            addChildProcesses(parentMap, ans, child);
        }
    }
}
```
- Runtime: 23 ms (Beats: 90.72%)
- Memory: 50.81 MB (Beats: 81.70%)

<br>
