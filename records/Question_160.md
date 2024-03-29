# [LeetCode Records](../README.md) - Question 160 Intersection of Two Linked Lists

### Attempt 1: 
```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        HashSet<ListNode> hashSet = new HashSet<>();

        ListNode currA = headA;
        ListNode currB = headB;
        while (currA != null && currB != null) {
            if (hashSet.contains(currA)) {
                return currA;
            } else {
                hashSet.add(currA);
            }

            if (hashSet.contains(currB)) {
                return currB;
            } else {
                hashSet.add(currB);
            }

            currA = currA.next;
            currB = currB.next;
        }

        while (currA != null) {
            if (hashSet.contains(currA)) {
                return currA;
            } else {
                hashSet.add(currA);
            }

            currA = currA.next;
        }
        while (currB != null) {
            if (hashSet.contains(currB)) {
                return currB;
            } else {
                hashSet.add(currB);
            }

            currB = currB.next;
        }

        return null;
    }
}
```
- Runtime: 9 ms (Beats: 14.31%)
- Memory: 47.61 MB (Beats: 92.93%)

<br>

### Attempt 2: Calculate the size of each list first
```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        int countA = 0;
        int countB = 0;
        ListNode currA = headA;
        ListNode currB = headB;

        while (currA != null) {
            currA = currA.next;
            countA++;
        }
        while (currB != null) {
            currB = currB.next;
            countB++;
        }

        while (countA > countB) {
            headA = headA.next;
            countA--;
        }
        while (countA < countB) {
            headB = headB.next;
            countB--;
        }

        while (headA != headB) {
            headA = headA.next;
            headB = headB.next;
        }

        return headA;
    }
}
```
- Runtime: 1 ms (Beats: 99.96%)
- Memory: 48.38 MB (Beats: 66.11%)

<br>
