# [LeetCode Records](../README.md) - Question 99 Recover Binary Search Tree

### Attempt 1: Use an int array and a HashMap to record the order of nodes
```java
class Solution {
    private int[] saved = new int[1000];
    private Map<Integer, TreeNode> map = new HashMap<>();
    private int size = 0;
    
    public void recoverTree(TreeNode root) {
        recoverTreeRecursion(root);

        int index1 = 0;
        for (int i = 0; i < size - 1; i++) {
            if (saved[i] > saved[i + 1] ) {
                index1 = i;
                break;
            }
        }

        int index2 = 0;
        for (int i = size - 1; i >= index1; i--) {
            if (saved[i] < saved[index1]) {
                index2 = i;
                break;
            }
        }

        TreeNode t1 = map.get(index1);
        TreeNode t2 = map.get(index2);
        int temp = t1.val;
        t1.val = t2.val;
        t2.val = temp;
    }

    private void recoverTreeRecursion(TreeNode root) {
        if (root == null) {
            return;
        } else if (root.left == null && root.right == null) {
            saved[size] = root.val;
            map.put(size, root);
            size++;
            return;
        }

        recoverTreeRecursion((root.left));
        saved[size] = root.val;
        map.put(size, root);
        size++;
        recoverTreeRecursion(root.right);
    }
}
```
- Runtime: 4 ms (Beats: 7.23%)
- Memory: 44.95 MB (Beats: 7.10%)

<br>

### Attempt 2: Use an int array to record the order of nodes
```java
class Solution {
    private int[] saved = new int[1000];

    private int size = 0;

    public void recoverTree(TreeNode root) {
        searchTreeRecursion(root);

        int index1 = 0;
        for (int i = 0; i < size - 1; i++) {
            if (saved[i] > saved[i + 1] ) {
                index1 = i;
                break;
            }
        }

        int index2 = 0;
        for (int i = size - 1; i >= index1; i--) {
            if (saved[i] < saved[index1]) {
                index2 = i;
                break;
            }
        }

        recoverTreeRecursion(root, saved[index1], saved[index2]);
    }

    private void searchTreeRecursion(TreeNode root) {
        if (root == null) {
            return;
        } else if (root.left == null && root.right == null) {
            saved[size++] = root.val;
            return;
        }

        searchTreeRecursion((root.left));
        saved[size++] = root.val;
        searchTreeRecursion(root.right);
    }

    private void recoverTreeRecursion(TreeNode root, int a, int b) {
        if (root == null) {
            return;
        } else if (root.val == a) {
            root.val = b;
        } else if (root.val == b) {
            root.val = a;
        }

        recoverTreeRecursion(root.left, a, b);
        recoverTreeRecursion(root.right, a, b);
    }
}
```
- Runtime: 3 ms (Beats: 12.61%)
- Memory: 44.66 MB (Beats: 20.07%)

<br>
