# [LeetCode Records](../../README.md) - Question 2807 Insert Greatest Common Divisors in Linked List

### Attempt 1: Use a helper function to get the greastest common divisor node
```java
class Solution {
    public ListNode insertGreatestCommonDivisors(ListNode head) {
        ListNode leftNode = head;
        ListNode rightNode = leftNode.next;

        while (rightNode != null) {
            ListNode middleNode = getGreatestCommonDivisorNode(leftNode.val, rightNode.val);
            leftNode.next = middleNode;
            middleNode.next = rightNode;

            leftNode = rightNode;
            rightNode = leftNode.next;
        }

        return head;
    }

    private ListNode getGreatestCommonDivisorNode(int num1, int num2) {
        int min = Math.min(num1, num2);
        
        int i = min;
        while (i > 1) {
            if (num1 % i == 0 && num2 % i == 0) {
                break;
            }

            i--;
        }

        return new ListNode(i);
    }
}
```
- Runtime: 22 ms (Beats: 33.22%)
- Memory: 45.02 MB (Beats: 31.36%)

<br>
