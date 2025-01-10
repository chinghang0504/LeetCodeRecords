# [LeetCode Records](../../README.md) - Question 323 Number of Connected Components in an Undirected Graph

### Attempt 1: Use a HashSet to store the node in the same components
```java
class Solution {
    public int countComponents(int n, int[][] edges) {
        Set<Integer> nodeSet = new HashSet<>();
        List<Set<Integer>> componentList = new ArrayList<>();
        for (int[] edge : edges) {
            nodeSet.add(edge[0]);
            nodeSet.add(edge[1]);

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

        return componentList.size() + n - nodeSet.size();
    }
}
```
- Runtime: 28 ms (Beats: 5.03%)
- Memory: 45.92 MB (Beats: 11.73%)

<br>
