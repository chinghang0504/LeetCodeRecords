# [LeetCode Records](../../README.md) - Question 2685 Count the Number of Complete Components

### Attempt 1: Use a HashSet to store all the nodes in the same component
```java
class Solution {
    public int countCompleteComponents(int n, int[][] edges) {
        int[] counts = new int[n];
        List<Set<Integer>> componentList = new ArrayList<>();
        for (int[] edge : edges) {
            counts[edge[0]]++;
            counts[edge[1]]++;

            List<Set<Integer>> list = new ArrayList<>();
            for (Set<Integer> component : componentList) {
                if (component.contains(edge[0]) || component.contains(edge[1])) {
                    list.add(component);
                }
            }

            int listSize = list.size();
            if (listSize == 0) {
                Set<Integer> component = new HashSet<>();
                component.add(edge[0]);
                component.add(edge[1]);
                componentList.add(component);
            } else if (listSize == 1) {
                Set<Integer> component = list.get(0);
                component.add(edge[0]);
                component.add(edge[1]);
            } else {
                Set<Integer> component1 = list.get(0);
                Set<Integer> component2 = list.get(1);
                if (component1 != component2) {
                    component1.addAll(component2);
                    componentList.remove(component2);
                }
            }
        }

        int completedComponentCount = 0;
        for (int i = 0; i < n; i++) {
            if (counts[i] == 0) {
                completedComponentCount++;
            }
        }

        for (Set<Integer> component : componentList) {
            boolean isCompleted = true;
            int targetCount = component.size() - 1;
            for (int node : component) {
                if (counts[node] != targetCount) {
                    isCompleted = false;
                    break;
                }
            }

            if (isCompleted) {
                completedComponentCount++;
            }
        }

        return completedComponentCount;
    }
}
```
- Runtime: 21 ms (Beats: 21.95%)
- Memory: 44.90 MB (Beats: 85.64%)

<br>
