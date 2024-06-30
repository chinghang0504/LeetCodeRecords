# [LeetCode Records](../../README.md) - Question 3062 Winner of the Linked List Game

### Attempt 1: Use two variables to store the sum
```java
class Solution {
    public String gameResult(ListNode head) {
        int evenSum = 0;
        int oddSum = 0;

        ListNode curr = head;
        while (curr != null) {
            int evenVal = curr.val;
            curr = curr.next;
            int oddVal = curr.val;
            curr = curr.next;

            if (evenVal > oddVal) {
                evenSum++;
            } else if (oddVal > evenVal) {
                oddSum++;
            }
        }

        if (evenSum == oddSum) {
            return "Tie";
        } else if (evenSum > oddSum) {
            return "Even";
        } else {
            return "Odd";
        }
    }
}
```
- Runtime: 1 ms (Beats: 72.52%)
- Memory: 44.55 MB (Beats: 8.40%)

<br>

### Attempt 2: Use one variable to store the sum
```java
class Solution {
    public String gameResult(ListNode head) {
        int sum = 0;

        ListNode curr = head;
        while (curr != null) {
            int evenVal = curr.val;
            curr = curr.next;
            int oddVal = curr.val;
            curr = curr.next;

            if (evenVal > oddVal) {
                sum++;
            } else if (oddVal > evenVal) {
                sum--;
            }
        }

        if (sum == 0) {
            return "Tie";
        } 
        return sum > 0 ? "Even" : "Odd";
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.07 MB (Beats: 58.78%)

<br>
