# [LeetCode Records](../../README.md) - Question 2326 Spiral Matrix IV

### Attempt 1: Use a boolean[][] to record which entries in reached
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public int[][] spiralMatrix(int m, int n, ListNode head) {
        int totalSteps = m * n;
        boolean[][] reached = new boolean[m][n];
        int[][] ans = new int[m][n];
        
        int step = 0;
        int i = 0;
        int j = 0;
        int direction = 0;
        ListNode curr = head;
        while (step < totalSteps) {
            reached[i][j] = true;
            if (curr == null) {
                ans[i][j] = -1;
            } else {
                ans[i][j] = curr.val;
                curr = curr.next;
            }

            int nextI = i;
            int nextJ = j;
            // Go right
            if (direction == 0) {
                nextJ = j + 1;
                if (nextJ >= n || reached[nextI][nextJ]) {
                    nextJ = j;
                    nextI = i + 1;
                    direction = 1;
                }
            }
            // Go down
            else if (direction == 1) {
                nextI = i + 1;
                if (nextI >= m || reached[nextI][nextJ]) {
                    nextI = i;
                    nextJ = j - 1;
                    direction = 2;
                }
            }
            // Go left
            else if (direction == 2) {
                nextJ = j - 1;
                if (nextJ < 0 || reached[nextI][nextJ]) {
                    nextJ = j;
                    nextI = i - 1;
                    direction = 3;
                }
            }
            // Go up
            else if (direction == 3) {
                nextI = i - 1;
                if (nextI < 0 || reached[nextI][nextJ]) {
                    nextI = i;
                    nextJ = j + 1;
                    direction = 0;
                }
            }

            i = nextI;
            j = nextJ;
            step++;
        }

        return ans;
    }
}
```
- Runtime: 15 ms (Beats: 7.74%)
- Memory: 61.25 MB (Beats: 11.77%)

<br>
