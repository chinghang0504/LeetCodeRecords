# [LeetCode Records](../../README.md) - Question 2359 Find Closest Node to Given Two Nodes

### Attempt 1: Use two HashMap to store the distances from root nodes
```java
class Solution {
    public int closestMeetingNode(int[] edges, int node1, int node2) {
        Map<Integer, Integer> nodeMap1 = getDistanceMap(edges, node1);
        Map<Integer, Integer> nodeMap2 = getDistanceMap(edges, node2);
        
        int maxDistance = Integer.MAX_VALUE;
        int minNode = -1;
        for (Map.Entry<Integer, Integer> entry1 : nodeMap1.entrySet()) {
            int commonNode = entry1.getKey();
            Integer distance2 = nodeMap2.get(commonNode);
            if (distance2 != null) {
                int distance1 = entry1.getValue();
                int currMaxDistance = Math.max(distance1, distance2);
                if (currMaxDistance < maxDistance) {
                    maxDistance = currMaxDistance;
                    minNode = commonNode;
                } else if (currMaxDistance == maxDistance) {
                    minNode = Math.min(minNode, commonNode);
                }
            }
        }

        return minNode;
    }

    private Map<Integer, Integer> getDistanceMap(int[] edges, int node) {
        Map<Integer, Integer> map = new HashMap<>();

        int distance = 0;
        int currNode = node;
        while (currNode != -1) {
            if (map.containsKey(currNode)) {
                return map;
            }
            
            map.put(currNode, distance);
            currNode = edges[currNode];
            distance++;
        }

        return map;
    }
}
```
- Runtime: 50 ms (Beats: 33.88%)
- Memory: 65.14 MB (Beats: 30.94%)

<br>
