# [LeetCode Records](../../README.md) - Question 1634 Add Two Polynomials Represented as Linked Lists

### Attempt 1: Use two pointers to track the current nodes
```java
/**
 * Definition for polynomial singly-linked list.
 * class PolyNode {
 *     int coefficient, power;
 *     PolyNode next = null;
 
 *     PolyNode() {}
 *     PolyNode(int x, int y) { this.coefficient = x; this.power = y; }
 *     PolyNode(int x, int y, PolyNode next) { this.coefficient = x; this.power = y; this.next = next; }
 * }
 */

class Solution {
    public PolyNode addPoly(PolyNode poly1, PolyNode poly2) {
        PolyNode dummy = new PolyNode();
        PolyNode curr = dummy;

        PolyNode curr1 = poly1;
        PolyNode curr2 = poly2;
        while (curr1 != null && curr2 != null) {
            if (curr1.power > curr2.power) {
                curr.next = curr1;
                curr = curr1;
                curr1 = curr1.next;
            } else if (curr1.power < curr2.power) {
                curr.next = curr2;
                curr = curr2;
                curr2 = curr2.next;
            } else {
                int coefficient = curr1.coefficient + curr2.coefficient;
                if (coefficient != 0) {
                    curr1.coefficient = coefficient;
                    curr.next = curr1;
                    curr = curr1;
                }
                curr1 = curr1.next;
                curr2 = curr2.next;
            }
        }
        curr.next = null;

        if (curr1 != null) {
            curr.next = curr1;
        } else if (curr2 != null) {
            curr.next = curr2;
        }

        return dummy.next;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 52.02 MB (Beats: 94.74%)

<br>
