# [LeetCode Records](../../README.md) - Question 234 Palindrome Linked List

### Attempt 1: Use a LinkedList
```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        List<Integer> list = new LinkedList<>();

        ListNode curr = head;
        while (curr != null) {
            list.add(curr.val);
            curr = curr.next;
        }

        list = list.reversed();
        Iterator<Integer> iterator = list.iterator();
        curr = head;
        while (iterator.hasNext() || curr != null) {
            if (iterator.next() != curr.val) {
                return false;
            }
            
            curr = curr.next;
        }
        
        return !iterator.hasNext() && curr == null;
    }
}
```
- Runtime: 13 ms (Beats: 16.25%)
- Memory: 61.41 MB (Beats: 61.14%)

<br>

### Attempt 2: Use an array
```java
class Solution {
    int[] arr = new int[100000];

    public boolean isPalindrome(ListNode head) {
        if (head == null && head.next == null) {
            return true;
        }

        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            arr[size++] = curr.val;
            curr = curr.next;
        }

        for (int i = 0; i < size / 2; i++) {
            if (arr[i] != arr[size - 1 - i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 5 ms (Beats: 60.37%)
- Memory: 63.14 MB (Beats: 59.56%)

<br>

### Attempt 3: Use a private static final array
```java
class Solution {
    private static final int[] arr = new int[100000];

    public boolean isPalindrome(ListNode head) {
        if (head == null && head.next == null) {
            return true;
        }

        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            arr[size++] = curr.val;
            curr = curr.next;
        }

        for (int i = 0; i < size / 2; i++) {
            if (arr[i] != arr[size - 1 - i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 99.40%)
- Memory: 65.08 MB (Beats: 54.33%)

<br>
