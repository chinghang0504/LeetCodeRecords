# [LeetCode Records](../../README.md) - Question 399 Evaluate Division

### Attempt 1: Use a HashMap to store the first variable and the node of the second variable and its value key-value pairs. Use dfs to search all related nodes
```java
class Solution {
    
    class Node {

        String variable;
        double value;

        Node(String variable, double value) {
            this.variable = variable;
            this.value = value;
        }
    }

    private Map<String, List<Node>> variableToNodes;
    
    public double[] calcEquation(List<List<String>> equations, double[] values, List<List<String>> queries) {
        variableToNodes = new HashMap<>();
        addEquations(variableToNodes, equations, values);

        int ansSize = queries.size();
        double[] ans = new double[ansSize];
        int ansIndex = 0;
        for (List<String> query : queries) {
            Double value = dfs(new HashSet<>(), query.getFirst(), query.getLast(), 1.0);
            ans[ansIndex++] = value == null ? -1.0 : value;
        }

        return ans;
    }

    private void addEquations(Map<String, List<Node>> variableToNodes, List<List<String>> equations, double[] values) {
        int i = 0;
        for (List<String> equation : equations) {
            String variable1 = equation.getFirst();
            String variable2 = equation.getLast();

            List<Node> nodes = variableToNodes.get(variable1);
            if (nodes == null) {
                nodes = new ArrayList<>();
                variableToNodes.put(variable1, nodes);
            }
            nodes.add(new Node(variable2, values[i]));

            nodes = variableToNodes.get(variable2);
            if (nodes == null) {
                nodes = new ArrayList<>();
                variableToNodes.put(variable2, nodes);
            }
            nodes.add(new Node(variable1, 1.0 / values[i]));

            i++;
        }
    }

    private Double dfs(Set<String> checkedVariable, String firstVariable, String lastVariable, double currVal) {
        if (checkedVariable.contains(firstVariable)) {
            return null;
        } else if (!variableToNodes.containsKey(firstVariable)) {
            return null;
        } else if (firstVariable.equals(lastVariable)) {
            return currVal;
        }
        checkedVariable.add(firstVariable);

        List<Node> nodes = variableToNodes.get(firstVariable);
        if (nodes == null) {
            return null;
        }
        for (Node node : nodes) {
            Double val = dfs(checkedVariable, node.variable, lastVariable, currVal);
            if (val != null) {
                return node.value * val;
            }
        }

        return null;
    }
}
```
- Runtime: 1 ms (Beats: 99.07%)
- Memory: 42.38 MB (Beats: 48.77%)

<br>
