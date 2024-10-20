# [LeetCode Records](../../README.md) - Question 43 Multiply Strings

### Attempt 1: Calculate the sum of multiplied by one digit
```java
class Solution {
    public String multiply(String num1, String num2) {
        char[] arr1 = num1.toCharArray();
        char[] arr2 = num2.toCharArray();
        List<List<Character>> lists = new ArrayList<>();

        for (int i = arr2.length - 1, j = 0; i >= 0; i--, j++) {
            lists.add(multiplyOneDigit(arr1, arr2[i] - '0', j));
        }

        int size = lists.size();
        List<Character> result = lists.get(0);
        for (int i = 1; i < size; i++) {
            result = sumOfTwo(result, lists.get(i));
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (char ch : result) {
            stringBuilder.append(ch);
        }

        return stringBuilder.toString();
    }

    private List<Character> multiplyOneDigit(char[] arr, int multiplier, int numOfZeros) {
        List<Character> list = new ArrayList<>();

        if (multiplier == 0) {
            list.addLast('0');
            return list;
        }

        int remainder = 0;
        for (int i = arr.length - 1; i >= 0; i--) {
            int val = (arr[i] - '0') * multiplier + remainder;
            if (val >= 10) {
                remainder = val / 10;
                val %= 10;
            } else {
                remainder = 0;
            }

            list.addFirst((char) (val + '0'));
        }
        if (remainder > 0) {
            list.addFirst((char) (remainder + '0'));
        }

        if (!(list.size() == 1 && list.get(0) == '0')) {
            for (int i = 0; i < numOfZeros; i++) {
                list.addLast('0');
            }
        }

        return list;
    }

    private List<Character> sumOfTwo(List<Character> list1, List<Character> list2) {
        int leftIndex = list1.size() - 1;
        int rightIndex = list2.size() - 1;
        List<Character> result = new ArrayList<>();

        int remainder = 0;
        while (leftIndex >= 0 && rightIndex >= 0) {
            int val = (list1.get(leftIndex) - '0') + (list2.get(rightIndex) - '0') + remainder;
            if (val >= 10) {
                val -= 10;
                remainder = 1;
            } else {
                remainder = 0;
            }

            result.addFirst((char) (val + '0'));
            leftIndex--;
            rightIndex--;
        }
        while (leftIndex >= 0) {
            int val = (list1.get(leftIndex) - '0') + remainder;
            if (val >= 10) {
                val -= 10;
                remainder = 1;
            } else {
                remainder = 0;
            }

            result.addFirst((char) (val + '0'));
            leftIndex--;
        }
        while (rightIndex >= 0) {
            int val = (list2.get(rightIndex) - '0') + remainder;
            if (val >= 10) {
                val -= 10;
                remainder = 1;
            } else {
                remainder = 0;
            }

            result.addFirst((char) (val + '0'));
            rightIndex--;
        }
        if (remainder > 0) {
            result.addFirst((char) (remainder + '0'));
        }

        return result;
    }
}
```
- Runtime: 18 ms (Beats: 7.05%)
- Memory: 45.32 MB (Beats: 5.43%)

<br>
