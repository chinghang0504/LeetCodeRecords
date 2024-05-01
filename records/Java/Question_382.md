# [LeetCode Records](../../README.md) - Question 382 Linked List Random Node

### Attempt 1: Use an ArrayList to record the numbers
```java
class Solution {

    private List<Integer> list;
    private int size;
    private Random random;

    public Solution(ListNode head) {
        this.list = new ArrayList<>();

        ListNode curr = head;
        while (curr != null) {
            this.list.add(curr.val);
            curr = curr.next;
        }

        this.size = this.list.size();
        this.random = new Random();
    }
    
    public int getRandom() {
        return this.list.get(random.nextInt(this.size));
    }
}
```
- Runtime: 11 ms (Beats: 64.45%)
- Memory: 45.80 MB (Beats: 70.87%)

<br>

### Attempt 2: Use an int array to record the numbers
```java
class Solution {

    private Random random = new Random();
    private int[] arr = new int[10000];
    private int size;

    public Solution(ListNode head) {
        ListNode curr = head;
        while (curr != null) {
            this.arr[this.size++] = curr.val;
            curr = curr.next;
        }
    }
    
    public int getRandom() {
        return this.arr[random.nextInt(this.size)];
    }
}
```
- Runtime: 10 ms (Beats: 92.43%)
- Memory: 45.42 MB (Beats: 95.41%)

<br>
