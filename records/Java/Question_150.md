# [LeetCode Records](../../README.md) - Question 150 Evaluate Reverse Polish Notation

### Attempt 1: Use an ArrayList to store the operands
```java
class Solution {
    public int evalRPN(String[] tokens) {
        List<Integer> list = new ArrayList<>();

        for (String token : tokens) {
            if (token.equals("+")) {
                int num2 = list.removeLast();
                int num1 = list.removeLast();
                list.addLast(num1 + num2);
            } else if (token.equals("-")) {
                int num2 = list.removeLast();
                int num1 = list.removeLast();
                list.addLast(num1 - num2);
            } else if (token.equals("*")) {
                int num2 = list.removeLast();
                int num1 = list.removeLast();
                list.addLast(num1 * num2);
            } else if (token.equals("/")) {
                int num2 = list.removeLast();
                int num1 = list.removeLast();
                list.addLast(num1 / num2);
            } else {
                list.addLast(Integer.valueOf(token));
            }
        }

        return list.getFirst();
    }
}
```
- Runtime: 5 ms (Beats: 97.92%)
- Memory: 44.54 MB (Beats: 54.76%)

<br>
