# [LeetCode Records](../../README.md) - Question 796 Rotate String

### Attempt 1: Use two LinkedList
```java
class Solution {
    public boolean rotateString(String s, String goal) {
        List<Character> list1 = new LinkedList<>();
        List<Character> list2 = new LinkedList<>();

        int size1 = s.length();
        int size2 = goal.length();
        if (size1 != size2) {
            return false;
        }

        for (char ch : s.toCharArray()) {
            list1.add(ch);
        }
        for (char ch : goal.toCharArray()) {
            list2.add(ch);
        }

        for (int i = 0; i < size1; i++) {
            if (list1.equals(list2)) {
                return true;
            } else {
                list1.add(list1.removeFirst());
            }
        }

        return false;
    }
}
```
- Runtime: 2 ms (Beats: 14.09%)
- Memory: 41.32 MB (Beats: 42.86%)

<br>

### Attempt 2: Use contains()
```java
class Solution {
    public boolean rotateString(String s, String goal) {
        int size1 = s.length();
        int size2 = goal.length();

        if (size1 != size2) {
            return false;
        }

        return (s + s).contains(goal);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.71 MB (Beats: 15.38%)

<br>
