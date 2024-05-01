# [LeetCode Records](../../README.md) - Question 111 Minimum Depth of Binary Tree

### Attempt 1: Use a ArrayList and a HashMap
```java
class Solution {
    public int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        List<TreeNode> list = new ArrayList<>();
        HashMap<TreeNode, Integer> hashMap = new HashMap<>();
        
        list.add(root);
        hashMap.put(root, 1);
        
        while (!list.isEmpty()) {
            TreeNode curr = list.removeFirst();
            int depth = hashMap.get(curr);
            
            if (curr.left == null && curr.right == null) {
                return depth;
            } else {
                if (curr.left != null) {
                    list.add(curr.left);
                    hashMap.put(curr.left, depth + 1);
                }
                if (curr.right != null) {
                    list.add(curr.right);
                    hashMap.put(curr.right, depth + 1);
                }
            }
        }

        return 0;
    }
}
```
- Runtime: 4 ms (Beats: 78.89%)
- Memory: 64.48 MB (Beats: 5.18%)

<br>

### Attempt 2: Use a ArrayList
```java
class Solution {
    public int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int depth = 1;
        List<TreeNode> list = new ArrayList<>();
        list.add(root);

        while (!list.isEmpty()) {
            int size = list.size();
            for (int i = 0; i < size; i++) {
                TreeNode curr = list.removeFirst();

                if (curr.left == null && curr.right == null) {
                    return depth;
                } else {
                    if (curr.left != null) {
                        list.add(curr.left);
                    }
                    if (curr.right != null) {
                        list.add(curr.right);
                    }
                }
            }
            depth++;
        }

        return -1;
    }
}
```
- Runtime: 2 ms (Beats: 92.66%)
- Memory: 62.29 MB (Beats: 98.76%)

<br>

### Attempt 3: Use a LinkedList and offer()
```java
class Solution {
    public int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int depth = 1;
        Queue<TreeNode> list = new LinkedList<>();
        list.offer(root);

        while (!list.isEmpty()) {
            int size = list.size();
            for (int i = 0; i < size; i++) {
                TreeNode curr = list.poll();

                if (curr.left == null && curr.right == null) {
                    return depth;
                } else {
                    if (curr.left != null) {
                        list.offer(curr.left);
                    }
                    if (curr.right != null) {
                        list.offer(curr.right);
                    }
                }
            }
            depth++;
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 99.85%)
- Memory: 63.14 MB (Beats: 55.94%)

<br>
