# [LeetCode Records](../../README.md) - Question 1415 The k-th Lexicographical String of All Happy Strings of Length n

### Attempt 1: Use a recursion to generate happy strings
```java
class Solution {
    public String getHappyString(int n, int k) {
        List<String> list = getHappyStringRecursion(n);

        return k > list.size() ? "" : list.get(k - 1);
    }

    private List<String> getHappyStringRecursion(int n) {
        if (n == 1) {
            return List.of("a", "b", "c");
        }

        List<String> prevList = getHappyStringRecursion(n - 1);
        List<String> list = new ArrayList<>();
        for (String str : prevList) {
            if (str.charAt(n - 2) == 'a') {
                list.add(str + "b");
                list.add(str + "c");
            } else if (str.charAt(n - 2) == 'b') {
                list.add(str + "a");
                list.add(str + "c");
            } else if (str.charAt(n - 2) == 'c') {
                list.add(str + "a");
                list.add(str + "b");
            }
        }

        return list;
    }
}
```
- Runtime: 18 ms (Beats: 34.92%)
- Memory: 45.14 MB (Beats: 21.70%)

<br>
