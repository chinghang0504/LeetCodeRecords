# [LeetCode Records](../../README.md) - Question 1404 Number of Steps to Reduce a Number in Binary Representation to One

### Attempt 1: Store the binary digits in the LinkedList
```java
class Solution {
    public int numSteps(String s) {
        List<Integer> list = new LinkedList<>();
        for (char ch : s.toCharArray()) {
            list.addLast(ch == '0' ? 0 : 1);
        }

        int count = 0;
        while (list.size() > 1) {
            if (list.getLast() == 0) {
                list.removeLast();
            } else {
                int remainder = 1;
                for (int i = list.size() - 1; i >= 0; i--) {
                    if (list.get(i) + remainder == 2) {
                        list.set(i, 0);
                        remainder = 1;
                    } else {
                        list.set(i, 1);
                        remainder = 0;
                        break;
                    }
                }
                if (remainder == 1) {
                    list.addFirst(1);
                }
            }

            count++;
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 22.15%)
- Memory: 41.59 MB (Beats: 35.62%)

<br>
