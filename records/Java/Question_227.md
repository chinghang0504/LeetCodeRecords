# [LeetCode Records](../../README.md) - Question 227 Basic Calculator II

### Attempt 1: Use an ArrayList to store the positive and the negative numbers
```java
class Solution {

    public int calculate(String s) {
        char[] arr = s.toCharArray();
        List<Integer> list = new ArrayList<>();

        int i = 0;
        while (i < arr.length) {
            while (i < arr.length && arr[i] == ' ') {
                i++;
            }
            if (i >= arr.length) {
                break;
            }

            int operator = 0;
            if (arr[i] == '+') {
                operator = 0;
                i++;
            } else if (arr[i] == '-') {
                operator = 1;
                i++;
            } else if (arr[i] == '*') {
                operator = 2;
                i++;
            } else if (arr[i] == '/') {
                operator = 3;
                i++;
            }

            while (arr[i] == ' ') {
                i++;
            }
            
            int num = 0;
            while (i < arr.length && Character.isDigit(arr[i])) {
                num = num * 10 + (arr[i] - '0');
                i++;
            }

            if (operator == 0) {
                list.add(num);
            } else if (operator == 1) {
                list.add(-1 * num);
            } else if (operator == 2) {
                list.add(list.removeLast() * num);
            } else if (operator == 3) {
                list.add(list.removeLast() / num);
            }
        }

        int sum = 0;
        for (int item : list) {
            sum += item;
        }

        return sum;
    }
}
```
- Runtime: 13 ms (Beats: 90.33%)
- Memory: 46.86 MB (Beats: 19.58%)

<br>
